# Supplier Info Record Data Extraction Guide

## Overview
This guide provides SQL queries to extract Supplier Info Record data from SAP ECC 6.0 for migration to SAP ERP Public Cloud. This includes general purchasing data and pricing conditions.

## Source Tables in SAP ECC 6.0

- **EINA**: Purchasing Info Record - General Data
- **EINE**: Purchasing Info Record - Purchasing Organization Data
- **A018**: Pricing Conditions for Supplier Info Records
- **KONP**: Condition Record Data (for pricing details)
- **LFA1**: Vendor Master (General Section)
- **MARA**: Material Master (General Data)
- **T024**: Purchasing Groups
- **T001**: Company Codes

## Extraction Queries

### 1. Supplier Info Record - General Data Extraction

Extract general supplier info record data from EINA table.

```sql
SELECT 
    e.INFNR as "Info Record Number",
    e.LIFNR as "Vendor Number",
    e.MATNR as "Material Number",
    e.MEINS as "Purchase Order Unit",
    e.UMREZ as "Numerator for UoM Conversion",
    e.UMREN as "Denominator for UoM Conversion",
    e.MAHN1 as "Reminder 1",
    e.MAHN2 as "Reminder 2",
    e.MAHN3 as "Reminder 3",
    e.URZLA as "Days Lead Time",
    e.NORM1 as "Standard Quantity 1",
    e.NORM2 as "Standard Quantity 2",
    e.NORM3 as "Standard Quantity 3",
    e.LTSNR as "Vendor Sub-range Number",
    e.ERDAT as "Created Date",
    e.ERNAM as "Created By",
    e.LOEKZ as "Deletion Flag",
    v.NAME1 as "Vendor Name",
    m.MAKTX as "Material Description"
FROM 
    EINA e
    LEFT JOIN LFA1 v ON e.LIFNR = v.LIFNR
    LEFT JOIN MAKT m ON e.MATNR = m.MATNR AND m.SPRAS = 'E'
WHERE 
    e.LOEKZ = ''  -- Not deleted
ORDER BY 
    e.LIFNR, e.MATNR;
```

### 2. Supplier Info Record - Purchasing Org Data Extraction

Extract purchasing organization specific data from EINE table.

```sql
SELECT 
    ei.INFNR as "Info Record Number",
    ei.EKORG as "Purchasing Organization",
    ei.ESOKZ as "Purchasing Info Record Category",
    ei.WERKS as "Plant",
    ei.APLFZ as "Planned Delivery Time (days)",
    ei.EKGRP as "Purchasing Group",
    ei.NORBM as "Standard Quantity",
    ei.WAERS as "Currency",
    ei.NETPR as "Net Price",
    ei.PEINH as "Price Unit",
    ei.BPRME as "Order Price Unit",
    ei.PRDAT as "Price Date",
    ei.MWSKZ as "Tax Code",
    ei.BONUS as "Vendor Rebate Group",
    ei.INCO1 as "Incoterms Part 1",
    ei.INCO2 as "Incoterms Part 2",
    ei.UEBTO as "Over-delivery Tolerance %",
    ei.UNTTO as "Under-delivery Tolerance %",
    ei.UEBTK as "Unlimited Over-delivery",
    ei.MINBM as "Minimum Order Quantity",
    ei.BSTMA as "Maximum Order Quantity",
    ei.EVERS as "Shipping Instructions",
    ei.WEBRE as "GR-Based Invoice Verification",
    ei.LOEKZ as "Deletion Flag",
    ei.ERDAT as "Created Date",
    ei.ERNAM as "Created By",
    pg.EKNAM as "Purchasing Group Name"
FROM 
    EINE ei
    LEFT JOIN T024 pg ON ei.EKGRP = pg.EKGRP
WHERE 
    ei.LOEKZ = ''  -- Not deleted
ORDER BY 
    ei.INFNR, ei.EKORG, ei.WERKS;
```

### 3. Complete Supplier Info Record (Combined EINA + EINE)

Full supplier info record with general and purchasing org data combined.

```sql
SELECT 
    ea.INFNR as "Info Record Number",
    ea.LIFNR as "Vendor Number",
    ea.MATNR as "Material Number",
    ei.EKORG as "Purchasing Organization",
    ei.WERKS as "Plant",
    ei.ESOKZ as "Info Record Category",
    ea.MEINS as "Order Unit",
    ei.NORBM as "Standard Quantity",
    ei.APLFZ as "Planned Delivery Time",
    ei.EKGRP as "Purchasing Group",
    ei.NETPR as "Net Price",
    ei.PEINH as "Price Unit",
    ei.WAERS as "Currency",
    ei.PRDAT as "Price Date",
    ei.MWSKZ as "Tax Code",
    ei.INCO1 as "Incoterms 1",
    ei.INCO2 as "Incoterms 2",
    ei.MINBM as "Min Order Qty",
    ei.BSTMA as "Max Order Qty",
    ei.UEBTO as "Over-delivery Tolerance",
    ei.UNTTO as "Under-delivery Tolerance",
    ei.WEBRE as "GR-Based IV",
    ea.ERDAT as "Created Date",
    ea.ERNAM as "Created By",
    v.NAME1 as "Vendor Name",
    m.MAKTX as "Material Description"
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
    LEFT JOIN LFA1 v ON ea.LIFNR = v.LIFNR
    LEFT JOIN MAKT m ON ea.MATNR = m.MATNR AND m.SPRAS = 'E'
WHERE 
    ea.LOEKZ = ''
    AND ei.LOEKZ = ''
    AND ei.EKORG IN ('1000', '2000')  -- Replace with your purchasing orgs
ORDER BY 
    ea.LIFNR, ea.MATNR, ei.EKORG, ei.WERKS;
```

### 4. Pricing Conditions Extraction (from A018 and KONP)

Extract pricing conditions for supplier info records.

```sql
SELECT 
    a.KAPPL as "Application",
    a.KSCHL as "Condition Type",
    a.LIFNR as "Vendor Number",
    a.MATNR as "Material Number",
    a.EKORG as "Purchasing Organization",
    a.WERKS as "Plant",
    a.ESOKZ as "Purchasing Info Record Category",
    a.KNUMH as "Condition Record Number",
    a.DATBI as "Valid To Date",
    a.DATAB as "Valid From Date",
    k.KOPOS as "Condition Item Number",
    k.KBETR as "Condition Amount",
    k.KONWA as "Condition Currency",
    k.KPEIN as "Condition Pricing Unit",
    k.KMEIN as "Condition Unit",
    k.LOEVM_KO as "Deletion Indicator"
FROM 
    A018 a
    INNER JOIN KONP k ON a.KNUMH = k.KNUMH
WHERE 
    a.KAPPL = 'M'  -- Purchasing application
    AND a.KSCHL IN ('PB00', 'ZP01', 'ZP02')  -- Common price condition types (adjust as needed)
    AND a.DATBI >= CURRENT_DATE  -- Valid conditions only
    AND k.LOEVM_KO = ''  -- Not deleted
ORDER BY 
    a.LIFNR, a.MATNR, a.KSCHL, a.DATAB DESC;
```

### 5. Supplier Info Record with Pricing

Complete extraction with pricing conditions joined.

```sql
SELECT 
    ea.INFNR as "Info Record Number",
    ea.LIFNR as "Vendor Number",
    ea.MATNR as "Material Number",
    ei.EKORG as "Purchasing Organization",
    ei.WERKS as "Plant",
    ei.ESOKZ as "Info Category",
    ei.EKGRP as "Purchasing Group",
    ei.NETPR as "Info Record Net Price",
    ei.WAERS as "Info Record Currency",
    ei.PEINH as "Info Record Price Unit",
    a.KSCHL as "Condition Type",
    k.KBETR as "Condition Price",
    k.KONWA as "Condition Currency",
    k.KPEIN as "Condition Price Unit",
    k.KMEIN as "Condition Unit",
    a.DATAB as "Condition Valid From",
    a.DATBI as "Condition Valid To",
    ei.APLFZ as "Delivery Time Days",
    ei.MINBM as "Min Order Qty",
    ei.INCO1 as "Incoterms 1",
    v.NAME1 as "Vendor Name",
    m.MAKTX as "Material Description"
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
    LEFT JOIN A018 a ON 
        ea.LIFNR = a.LIFNR 
        AND ea.MATNR = a.MATNR
        AND ei.EKORG = a.EKORG
        AND ei.WERKS = a.WERKS
        AND ei.ESOKZ = a.ESOKZ
        AND a.KAPPL = 'M'
        AND a.DATBI >= CURRENT_DATE
    LEFT JOIN KONP k ON a.KNUMH = k.KNUMH AND k.LOEVM_KO = ''
    LEFT JOIN LFA1 v ON ea.LIFNR = v.LIFNR
    LEFT JOIN MAKT m ON ea.MATNR = m.MATNR AND m.SPRAS = 'E'
WHERE 
    ea.LOEKZ = ''
    AND ei.LOEKZ = ''
ORDER BY 
    ea.LIFNR, ea.MATNR, ei.EKORG, a.KSCHL;
```

### 6. Supplier Info Record Validation Pre-Check Query

Identify potential data quality issues before extraction.

```sql
-- Check for info records with missing or invalid data
SELECT 
    'Missing Vendor' as "Issue Type",
    e.INFNR as "Info Record Number",
    e.LIFNR as "Vendor Number",
    e.MATNR as "Material Number",
    '' as "Details"
FROM 
    EINA e
WHERE 
    (e.LIFNR IS NULL OR e.LIFNR = '')
    AND e.LOEKZ = ''

UNION ALL

SELECT 
    'Missing Material' as "Issue Type",
    e.INFNR,
    e.LIFNR,
    e.MATNR,
    ''
FROM 
    EINA e
WHERE 
    (e.MATNR IS NULL OR e.MATNR = '')
    AND e.LOEKZ = ''

UNION ALL

SELECT 
    'Invalid Order Unit' as "Issue Type",
    e.INFNR,
    e.LIFNR,
    e.MATNR,
    e.MEINS as "Details"
FROM 
    EINA e
WHERE 
    (e.MEINS IS NULL OR e.MEINS = '')
    AND e.LOEKZ = ''

UNION ALL

SELECT 
    'Missing Purchasing Org Data' as "Issue Type",
    ea.INFNR,
    ea.LIFNR,
    ea.MATNR,
    'No EINE record'
FROM 
    EINA ea
WHERE 
    ea.LOEKZ = ''
    AND NOT EXISTS (SELECT 1 FROM EINE ei WHERE ei.INFNR = ea.INFNR AND ei.LOEKZ = '')

UNION ALL

SELECT 
    'Zero or Negative Price' as "Issue Type",
    ea.INFNR,
    ea.LIFNR,
    ea.MATNR,
    CAST(ei.NETPR AS VARCHAR(20))
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
WHERE 
    ei.NETPR <= 0
    AND ei.LOEKZ = ''

UNION ALL

SELECT 
    'Missing Currency' as "Issue Type",
    ea.INFNR,
    ea.LIFNR,
    ea.MATNR,
    ei.WAERS
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
WHERE 
    (ei.WAERS IS NULL OR ei.WAERS = '')
    AND ei.NETPR > 0
    AND ei.LOEKZ = ''

UNION ALL

SELECT 
    'Expired Price Date' as "Issue Type",
    ea.INFNR,
    ea.LIFNR,
    ea.MATNR,
    CAST(ei.PRDAT AS VARCHAR(10))
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
WHERE 
    ei.PRDAT < CURRENT_DATE
    AND ei.NETPR > 0
    AND ei.LOEKZ = '';
```

### 7. Supplier Info Record Count Summary

Get counts for reconciliation purposes.

```sql
SELECT 
    'Total Info Records (EINA)' as "Count Type",
    COUNT(*) as "Count"
FROM 
    EINA
WHERE 
    LOEKZ = ''

UNION ALL

SELECT 
    'Total Purchasing Org Records (EINE)' as "Count Type",
    COUNT(*) as "Count"
FROM 
    EINE
WHERE 
    LOEKZ = ''

UNION ALL

SELECT 
    'Unique Vendors with Info Records' as "Count Type",
    COUNT(DISTINCT LIFNR) as "Count"
FROM 
    EINA
WHERE 
    LOEKZ = ''

UNION ALL

SELECT 
    'Unique Materials with Info Records' as "Count Type",
    COUNT(DISTINCT MATNR) as "Count"
FROM 
    EINA
WHERE 
    LOEKZ = ''

UNION ALL

SELECT 
    'Info Records by Purchasing Org' as "Count Type",
    COUNT(*) as "Count"
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
WHERE 
    ea.LOEKZ = ''
    AND ei.LOEKZ = ''

UNION ALL

SELECT 
    'Info Records with Pricing Conditions' as "Count Type",
    COUNT(DISTINCT ea.INFNR) as "Count"
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
    INNER JOIN A018 a ON 
        ea.LIFNR = a.LIFNR 
        AND ea.MATNR = a.MATNR
        AND ei.EKORG = a.EKORG
WHERE 
    ea.LOEKZ = ''
    AND ei.LOEKZ = ''
    AND a.DATBI >= CURRENT_DATE;
```

### 8. Purchasing Organizations and Plants Breakdown

Understand the scope by purchasing organization and plant.

```sql
SELECT 
    ei.EKORG as "Purchasing Organization",
    ei.WERKS as "Plant",
    COUNT(DISTINCT ea.INFNR) as "Info Record Count",
    COUNT(DISTINCT ea.LIFNR) as "Unique Vendors",
    COUNT(DISTINCT ea.MATNR) as "Unique Materials",
    AVG(ei.NETPR) as "Average Price"
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
WHERE 
    ea.LOEKZ = ''
    AND ei.LOEKZ = ''
GROUP BY 
    ei.EKORG, ei.WERKS
ORDER BY 
    ei.EKORG, ei.WERKS;
```

### 9. Info Records by Material Type

Breakdown of info records by material type for analysis.

```sql
SELECT 
    m.MTART as "Material Type",
    COUNT(DISTINCT ea.INFNR) as "Info Record Count",
    COUNT(DISTINCT ea.LIFNR) as "Unique Vendors",
    COUNT(DISTINCT ea.MATNR) as "Unique Materials"
FROM 
    EINA ea
    INNER JOIN MARA m ON ea.MATNR = m.MATNR
WHERE 
    ea.LOEKZ = ''
GROUP BY 
    m.MTART
ORDER BY 
    COUNT(DISTINCT ea.INFNR) DESC;
```

### 10. Recent Info Records (Last 6 Months)

Extract recently created or updated info records.

```sql
SELECT 
    ea.INFNR as "Info Record Number",
    ea.LIFNR as "Vendor Number",
    ea.MATNR as "Material Number",
    ei.EKORG as "Purchasing Organization",
    ei.WERKS as "Plant",
    ei.NETPR as "Net Price",
    ei.WAERS as "Currency",
    ea.ERDAT as "Created Date",
    ea.ERNAM as "Created By",
    v.NAME1 as "Vendor Name",
    m.MAKTX as "Material Description"
FROM 
    EINA ea
    INNER JOIN EINE ei ON ea.INFNR = ei.INFNR
    LEFT JOIN LFA1 v ON ea.LIFNR = v.LIFNR
    LEFT JOIN MAKT m ON ea.MATNR = m.MATNR AND m.SPRAS = 'E'
WHERE 
    ea.LOEKZ = ''
    AND ei.LOEKZ = ''
    AND ea.ERDAT >= ADD_MONTHS(CURRENT_DATE, -6)  -- Last 6 months
ORDER BY 
    ea.ERDAT DESC;
```

## Export Instructions

### Step 1: Execute Queries in SAP GUI (SE16/SE16N or SQVI)

1. Open transaction **SE16N** or **SQVI** in SAP ECC
2. Copy and paste the desired SQL query
3. Adjust the WHERE clause filters for your specific scope:
   - Purchasing Organizations (EKORG)
   - Plants (WERKS)
   - Date ranges
   - Vendor ranges
   - Material groups
4. Execute the query (F8)
5. Review the results for accuracy

### Step 2: Export to Excel/CSV

1. In the results screen, go to **System → List → Save → Local File**
2. Select format:
   - **Spreadsheet** (for Excel .xlsx)
   - **Unconverted** (for CSV)
3. Save the file with a descriptive name using this naming convention:
   - `SupplierInfo_General_YYYYMMDD.xlsx`
   - `SupplierInfo_PurchOrg_YYYYMMDD.xlsx`
   - `SupplierInfo_Combined_YYYYMMDD.xlsx`
   - `SupplierInfo_Pricing_YYYYMMDD.xlsx`

### Step 3: Data Preparation

1. Open the exported file in Excel
2. Remove any SAP GUI header/footer rows (usually first 1-3 rows)
3. Ensure column headers are in the first row
4. Check for special characters or formatting issues:
   - Material numbers with leading zeros
   - Vendor numbers with leading zeros
   - Decimal separators in prices
   - Date formats (YYYYMMDD)
5. Save a backup copy of the raw export
6. Save working copy as **CSV UTF-8** format for import processing

### Step 4: Split Large Files (if necessary)

If the extraction results in very large files (> 50,000 records):
1. Split by Purchasing Organization
2. Split by Plant
3. Split by Material Type
4. Keep consistent file naming: `SupplierInfo_[Org]_[Plant]_YYYYMMDD.xlsx`

## Sample Data Structure

### Supplier Info General Data Sample Output

| Info Record Number | Vendor Number | Material Number | Order Unit | Lead Time Days | Created Date | Vendor Name | Material Description |
|--------------------|---------------|-----------------|------------|----------------|--------------|-------------|---------------------|
| 5300000001 | 1000001 | MAT-12345 | EA | 14 | 20230115 | ABC Suppliers | Raw Material A |
| 5300000002 | 1000002 | MAT-12346 | KG | 21 | 20230120 | XYZ Vendors | Chemical B |

### Supplier Info Purchasing Org Data Sample Output

| Info Record Number | Purch Org | Plant | Planned Delivery | Net Price | Currency | Price Unit | Tax Code | Min Order Qty |
|--------------------|-----------|-------|------------------|-----------|----------|------------|----------|---------------|
| 5300000001 | 1000 | 1000 | 14 | 25.50 | USD | 1 | V0 | 10 |
| 5300000002 | 1000 | 1000 | 21 | 150.00 | USD | 1 | V0 | 50 |

### Pricing Conditions Sample Output

| Vendor Number | Material Number | Purch Org | Plant | Condition Type | Condition Price | Currency | Valid From | Valid To |
|---------------|-----------------|-----------|-------|----------------|-----------------|----------|------------|----------|
| 1000001 | MAT-12345 | 1000 | 1000 | PB00 | 25.50 | USD | 20230101 | 99991231 |
| 1000002 | MAT-12346 | 1000 | 1000 | PB00 | 150.00 | USD | 20230101 | 20231231 |

## Notes and Best Practices

### Query Execution
- Always run validation queries (Query #6) before extraction
- Test queries with small data sets first (add `FETCH FIRST 100 ROWS ONLY` or similar)
- Document the extraction date, time, and user ID
- Keep record counts for reconciliation
- Extract during off-peak hours to minimize system impact

### Data Scope
- Coordinate with purchasing teams to identify critical vendors and materials
- Consider extracting active info records first (recent price dates)
- Identify and handle info records with special pricing agreements
- Check for info records with quantity scales or tiered pricing

### Performance Considerations
- For large databases, add WHERE clause filters to limit scope
- Extract in batches by purchasing organization or vendor range
- Coordinate with SAP Basis team for large data volumes
- Consider using background jobs for very large extractions

### Data Quality
- Review validation query results before proceeding
- Document exceptions and get business approval
- Identify info records that require manual review
- Check for duplicate info records (same vendor-material-org-plant)

### Pricing Extraction
- Pricing conditions can be complex with multiple condition types
- Identify which condition types are used in your system
- Check for time-dependent pricing (valid from/to dates)
- Verify scale pricing if applicable (not shown in basic queries)

### Version Control
- Save all extraction files with date stamps
- Keep original extracts unchanged
- Work on copies for transformation
- Document any manual adjustments made

## Common Condition Types

Here are common purchasing condition types you may encounter:

| Condition Type | Description |
|---------------|-------------|
| PB00 | Gross Price |
| RB00 | Discount |
| ZP01 | Custom Price 1 |
| ZP02 | Custom Price 2 |
| FRB1 | Freight |
| NAVS | Non-deductible Input Tax |

**Note:** Your system may use different condition types. Check with your SAP team.

## Troubleshooting

### Query Execution Errors
- **Error:** "Table does not exist"
  - **Solution:** Verify table names, check authorizations
- **Error:** "Timeout"
  - **Solution:** Add more filters to WHERE clause, reduce scope
- **Error:** "No authorization"
  - **Solution:** Request SE16N and table-level read access from security team

### Data Issues
- **Issue:** Leading zeros missing from vendor/material numbers
  - **Solution:** Format cells as text before export, or use TEXT function in transformation
- **Issue:** Prices showing as zero
  - **Solution:** Check if prices are stored in KONP instead of EINE.NETPR
- **Issue:** Multiple prices for same info record
  - **Solution:** This is normal with condition records; include valid-to/from dates

## Related Transactions

- **ME11**: Create Info Record
- **ME12**: Change Info Record
- **ME13**: Display Info Record
- **ME1M**: Create Info Record (Vendor Known)
- **ME1L**: Create Info Record (Material Known)
- **SE16N**: General Table Display

## Document Version

- **Created:** [Date]
- **Last Updated:** [Date]
- **Project:** SAP ECC 6.0 to SAP ERP Public Cloud Migration
- **Author:** Migration Team


