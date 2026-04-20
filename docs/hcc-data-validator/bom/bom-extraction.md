# BOM Data Extraction Guide

## Overview
This guide provides SQL queries to extract Bill of Materials (BOM) data from SAP ECC 6.0 for migration to SAP ERP Public Cloud.

## Source Tables in SAP ECC 6.0

- **MAST**: Material to BOM Link
- **STKO**: BOM Header
- **STPO**: BOM Items
- **MARA**: Material Master
- **T001W**: Plants/Locations

## Extraction Queries

### 1. BOM Header Data Extraction

Extract BOM header information including material, plant, and usage details.

```sql
SELECT 
    m.MATNR as "Material Number",
    m.WERKS as "Plant",
    m.STLAN as "BOM Usage",
    m.STLNR as "BOM Number",
    m.STLAL as "Alternative BOM",
    s.STLTY as "BOM Category",
    s.BMENG as "Base Quantity",
    s.BMEIN as "Base Unit",
    s.STLST as "BOM Status",
    s.DATUV as "Valid From Date",
    s.ANDAT as "Created Date",
    s.ANNAM as "Created By",
    s.AEDAT as "Changed Date",
    s.AENAM as "Changed By",
    s.LOEKZ as "Deletion Flag",
    ma.MAKTX as "Material Description"
FROM 
    MAST m
    INNER JOIN STKO s ON m.STLNR = s.STLNR AND m.STLAL = s.STLAL
    LEFT JOIN MAKT ma ON m.MATNR = ma.MATNR AND ma.SPRAS = 'E'
WHERE 
    m.STLAN IN ('1', '2')  -- Production/Engineering BOM
    AND s.LOEKZ = ''  -- Not deleted
    AND s.STLST = '01'  -- Active status
ORDER BY 
    m.MATNR, m.WERKS, m.STLAN;
```

### 2. BOM Items Data Extraction

Extract BOM component items with quantities and positions.

```sql
SELECT 
    h.STLTY as "BOM Category",
    h.STLNR as "BOM Number",
    h.STLKN as "BOM Node Number",
    h.STPOZ as "Internal Counter",
    h.IDNRK as "Component Material",
    h.POSNR as "Item Number",
    h.POSTP as "Item Category",
    h.MENGE as "Component Quantity",
    h.MEINS as "Component Unit",
    h.AUSCH as "Component Scrap %",
    h.SANKA as "Costing Relevance",
    h.FMENG as "Fixed Quantity Indicator",
    h.AVOAU as "Operation Number",
    h.ALPRF as "Group Counter",
    h.ALPST as "Item Number Counter",
    h.EWAHR as "Usage Probability %",
    h.DATUV as "Valid From Date",
    h.DATUB as "Valid To Date",
    h.LOEKZ as "Deletion Flag",
    ma.MAKTX as "Component Description",
    h.ROMEI as "Component Scrap %"
FROM 
    STPO h
    LEFT JOIN MAKT ma ON h.IDNRK = ma.MATNR AND ma.SPRAS = 'E'
WHERE 
    h.LOEKZ = ''  -- Not deleted
    AND h.STLTY = 'M'  -- Material BOM
ORDER BY 
    h.STLNR, h.STLKN, h.POSNR;
```

### 3. Complete BOM Structure (Header + Items Combined)

Full BOM structure with parent-child relationships.

```sql
SELECT 
    m.MATNR as "Parent Material",
    m.WERKS as "Plant",
    m.STLAN as "BOM Usage",
    m.STLNR as "BOM Number",
    m.STLAL as "Alternative BOM",
    sk.BMENG as "Base Quantity",
    sk.BMEIN as "Base Unit",
    sp.POSNR as "Item Number",
    sp.IDNRK as "Component Material",
    sp.POSTP as "Item Category",
    sp.MENGE as "Component Quantity",
    sp.MEINS as "Component Unit",
    sp.AUSCH as "Component Scrap %",
    sp.AVOAU as "Operation Number",
    sp.DATUV as "Valid From Date",
    sp.DATUB as "Valid To Date",
    mp.MAKTX as "Parent Description",
    mc.MAKTX as "Component Description"
FROM 
    MAST m
    INNER JOIN STKO sk ON m.STLNR = sk.STLNR AND m.STLAL = sk.STLAL
    INNER JOIN STPO sp ON m.STLNR = sp.STLNR
    LEFT JOIN MAKT mp ON m.MATNR = mp.MATNR AND mp.SPRAS = 'E'
    LEFT JOIN MAKT mc ON sp.IDNRK = mc.MATNR AND mc.SPRAS = 'E'
WHERE 
    m.STLAN = '1'  -- Production BOM
    AND sk.LOEKZ = ''
    AND sp.LOEKZ = ''
    AND sk.STLST = '01'
ORDER BY 
    m.MATNR, m.WERKS, sp.POSNR;
```

### 4. BOM Validation Pre-Check Query

Identify potential data quality issues before extraction.

```sql
-- Check for BOMs with missing or invalid data
SELECT 
    'Missing Component Material' as "Issue Type",
    m.MATNR as "Parent Material",
    m.WERKS as "Plant",
    sp.POSNR as "Item Number",
    sp.IDNRK as "Component Material"
FROM 
    MAST m
    INNER JOIN STKO sk ON m.STLNR = sk.STLNR
    INNER JOIN STPO sp ON m.STLNR = sp.STLNR
WHERE 
    sp.IDNRK IS NULL OR sp.IDNRK = ''

UNION ALL

SELECT 
    'Zero or Negative Quantity' as "Issue Type",
    m.MATNR,
    m.WERKS,
    sp.POSNR,
    sp.IDNRK
FROM 
    MAST m
    INNER JOIN STKO sk ON m.STLNR = sk.STLNR
    INNER JOIN STPO sp ON m.STLNR = sp.STLNR
WHERE 
    sp.MENGE <= 0

UNION ALL

SELECT 
    'Missing Base Unit' as "Issue Type",
    m.MATNR,
    m.WERKS,
    '' as "Item Number",
    '' as "Component Material"
FROM 
    MAST m
    INNER JOIN STKO sk ON m.STLNR = sk.STLNR
WHERE 
    sk.BMEIN IS NULL OR sk.BMEIN = ''

UNION ALL

SELECT 
    'Expired BOM' as "Issue Type",
    m.MATNR,
    m.WERKS,
    sp.POSNR,
    sp.IDNRK
FROM 
    MAST m
    INNER JOIN STKO sk ON m.STLNR = sk.STLNR
    INNER JOIN STPO sp ON m.STLNR = sp.STLNR
WHERE 
    sp.DATUB < CURRENT_DATE
    AND sp.DATUB IS NOT NULL
    AND sp.DATUB != '99991231';
```

### 5. BOM Count Summary

Get counts for reconciliation purposes.

```sql
SELECT 
    'Total BOM Headers' as "Count Type",
    COUNT(DISTINCT m.STLNR) as "Count"
FROM 
    MAST m
    INNER JOIN STKO sk ON m.STLNR = sk.STLNR
WHERE 
    sk.LOEKZ = ''
    AND sk.STLST = '01'

UNION ALL

SELECT 
    'Total BOM Items' as "Count Type",
    COUNT(*) as "Count"
FROM 
    STPO sp
WHERE 
    sp.LOEKZ = ''

UNION ALL

SELECT 
    'Unique Parent Materials' as "Count Type",
    COUNT(DISTINCT m.MATNR) as "Count"
FROM 
    MAST m
    INNER JOIN STKO sk ON m.STLNR = sk.STLNR
WHERE 
    sk.LOEKZ = ''

UNION ALL

SELECT 
    'Unique Component Materials' as "Count Type",
    COUNT(DISTINCT sp.IDNRK) as "Count"
FROM 
    STPO sp
WHERE 
    sp.LOEKZ = '';
```

## Export Instructions

### Step 1: Execute Queries in SAP GUI (SE16/SE16N or SQVI)

1. Open transaction **SE16N** or **SQVI**
2. Copy and paste the desired SQL query
3. Execute the query (F8)
4. Review the results

### Step 2: Export to Excel/CSV

1. In the results screen, go to **System → List → Save → Local File**
2. Select format: **Spreadsheet** (for Excel) or **Unconverted** (for CSV)
3. Save the file with a descriptive name:
   - `BOM_Headers_YYYYMMDD.xlsx`
   - `BOM_Items_YYYYMMDD.xlsx`
   - `BOM_Full_YYYYMMDD.xlsx`

### Step 3: Data Preparation

1. Open the exported file
2. Remove any SAP GUI header/footer rows
3. Ensure column headers are in the first row
4. Check for special characters or formatting issues
5. Save as CSV UTF-8 format for import processing

## Sample Data Structure

### BOM Header Sample Output

| Material Number | Plant | BOM Usage | BOM Number | Alternative BOM | Base Quantity | Base Unit | BOM Status |
|----------------|-------|-----------|------------|-----------------|---------------|-----------|------------|
| FG-001 | 1000 | 1 | 00001234 | 01 | 1 | EA | 01 |
| FG-002 | 1000 | 1 | 00001235 | 01 | 1 | EA | 01 |

### BOM Items Sample Output

| BOM Number | Item Number | Component Material | Item Category | Component Quantity | Component Unit | Component Scrap % |
|------------|-------------|-------------------|---------------|-------------------|----------------|------------------|
| 00001234 | 0010 | RM-001 | L | 2.5 | KG | 5 |
| 00001234 | 0020 | RM-002 | L | 1.0 | L | 0 |

## Notes

- Always run validation queries before extraction
- Document the extraction date and time
- Keep record counts for reconciliation
- Extract data during off-peak hours to minimize system impact
- Coordinate with SAP Basis team for large data volumes

