# BOM Validation Procedures

## Overview
This document provides detailed validation procedures for BOM data migration from SAP ECC 6.0 to SAP ERP Public Cloud.

## Process Flow Diagram

For a visual overview of the validation process, see: [`bom-validation-process-flow.mmd`](bom-validation-process-flow.mmd)

The diagram shows the complete flow from receiving data files through go-live, including:
- All validation stages and checks
- Decision points (pass/fail criteria)
- Corrective action loops
- Stage progression logic

## Validation Stages

1. **Pre-Extraction Validation** - Check data quality in extracted files
2. **Template Validation** - Verify data in migration templates
3. **Post-Import Validation** - Confirm data accuracy in target system
4. **Reconciliation** - Ensure completeness and integrity

---

## Stage 1: Pre-Extraction Validation (Extracted Data Files)

**Note:** This stage assumes you have received extracted data files from the ECC team. You do not need direct ECC access.

### What to Request from ECC Team

Before validation, ensure the ECC team provides these files:
- `BOM_Headers_Extract_[DATE].xlsx` - BOM header data
- `BOM_Items_Extract_[DATE].xlsx` - BOM item data
- `BOM_Extract_Counts_[DATE].xlsx` - Count summary for reconciliation

Files should be in Excel (.xlsx) or CSV (.csv) format with column headers in the first row.

### Validation 1.1: BOM Header Data Quality

**Objective:** Identify BOMs with missing or invalid header data

**Method 1: Using Excel**

1. Open file: `BOM_Headers_Extract_[DATE].xlsx`
2. Add a new column called "Validation_Issue" 
3. In the first data row (usually row 2), add this formula:

```excel
=IF(OR(ISBLANK(D2), D2<=0), "Invalid/Missing Base Quantity", 
   IF(OR(ISBLANK(E2), E2=""), "Missing Base Unit", "OK"))
```

4. Copy formula down to all rows
5. Filter column "Validation_Issue" to show only rows that are NOT "OK"
6. Count the issues

**Method 2: Using Python (Pseudo Code)**

```
LOAD extracted file 'BOM_Headers_Extract_[DATE].xlsx' into dataframe

INITIALIZE empty issues list

CHECK Base Quantity field:
  FIND all rows WHERE Base Quantity is NULL OR Base Quantity <= 0
  IF found:
    ADD to issues list: "Invalid/Missing Base Quantity: [count] records"
    DISPLAY problematic records showing: Material, Plant, BOM Number, Base Quantity

CHECK Base Unit field:
  FIND all rows WHERE Base Unit is NULL OR Base Unit is empty string
  IF found:
    ADD to issues list: "Missing Base Unit: [count] records"
    DISPLAY problematic records showing: Material, Plant, BOM Number, Base Unit

DISPLAY total number of issues found
```

**Pass Criteria:** Zero issues found  
**Action if Failed:** Send list of problematic records back to ECC team for correction

### Validation 1.2: BOM Item Data Quality

**Objective:** Identify BOM items with missing or invalid data

**Method 1: Using Excel**

1. Open file: `BOM_Items_Extract_[DATE].xlsx`
2. Add a new column called "Validation_Issue"
3. In the first data row, add this formula:

```excel
=IF(OR(ISBLANK(C2), C2=""), "Missing Component",
   IF(OR(ISBLANK(D2), D2<=0), "Invalid Quantity",
   IF(OR(ISBLANK(E2), E2=""), "Missing Unit",
   IF(OR(ISBLANK(B2), B2=""), "Missing Item Number", "OK"))))
```

4. Copy formula down to all rows
5. Filter to show only rows that are NOT "OK"

**Method 2: Using Python (Pseudo Code)**

```
LOAD extracted file 'BOM_Items_Extract_[DATE].xlsx' into dataframe

DISPLAY header "BOM Item Data Quality Issues"

CHECK 1: Missing Component
  FIND all rows WHERE Component is NULL OR Component is empty string
  COUNT and DISPLAY: "Missing Component: [count] records"

CHECK 2: Invalid Quantity
  FIND all rows WHERE Quantity is NULL OR Quantity <= 0
  COUNT and DISPLAY: "Invalid Quantity: [count] records"

CHECK 3: Missing Unit
  FIND all rows WHERE Unit is NULL OR Unit is empty string
  COUNT and DISPLAY: "Missing Unit: [count] records"

CHECK 4: Missing Item Number
  FIND all rows WHERE Item Number is NULL OR Item Number is empty string
  COUNT and DISPLAY: "Missing Item Number: [count] records"

COMBINE all problematic rows from all checks (remove duplicates)
EXPORT combined issues to file 'BOM_Items_Issues.xlsx'
DISPLAY total count of problematic records
```

**Pass Criteria:** Zero issues found  
**Action if Failed:** Send issue file to ECC team or exclude problematic records from migration

### Validation 1.3: Component Material Master Existence

**Objective:** Verify all component materials exist in material master

**Prerequisites:** Request a material master list from ECC team:
- File: `Material_Master_List_[DATE].xlsx`
- Required column: Material Number

**Method 1: Using Excel with VLOOKUP**

1. Open `BOM_Items_Extract_[DATE].xlsx`
2. Open `Material_Master_List_[DATE].xlsx` in a second sheet
3. Add column "Material_Exists" in BOM Items sheet
4. Use this formula:

```excel
=IF(ISNA(VLOOKUP(C2, Material_Master_List!A:A, 1, FALSE)), "Material NOT Found", "OK")
```

5. Filter to show "Material NOT Found"

**Method 2: Using Python (Pseudo Code)**

```
LOAD 'BOM_Items_Extract_[DATE].xlsx' into bom_items dataframe
LOAD 'Material_Master_List_[DATE].xlsx' into materials dataframe

GET unique list of all components from bom_items
GET unique list of all material numbers from materials dataframe

COMPARE the two lists:
  FOR EACH component in BOM items:
    IF component NOT IN material master list:
      ADD to missing_materials list

DISPLAY "Total unique components in BOMs: [count]"
DISPLAY "Materials missing from material master: [count]"

IF missing materials found:
  FILTER bom_items to show only records with missing materials
  EXPORT filtered records to 'Missing_Component_Materials.xlsx'
  DISPLAY list of missing materials
  DISPLAY export confirmation message
```

**Pass Criteria:** All components exist in material master, or all missing materials documented  
**Action if Failed:** Request ECC team to provide missing material data, or plan to create them in Public Cloud first

### Validation 1.4: Duplicate BOM Item Numbers

**Objective:** Identify duplicate item numbers within same BOM

**Method 1: Using Excel Pivot Table**

1. Open `BOM_Items_Extract_[DATE].xlsx`
2. Create a pivot table:
   - Rows: BOM Number, Item Number
   - Values: Count of Item Number
3. Filter to show counts > 1
4. These are duplicates

**Method 2: Using Python (Pseudo Code)**

```
LOAD 'BOM_Items_Extract_[DATE].xlsx' into dataframe

GROUP BY 'BOM Number' and 'Item Number':
  COUNT occurrences of each combination
  KEEP only groups WHERE count > 1

DISPLAY "Duplicate item numbers found: [count]"

IF duplicates found:
  DISPLAY duplicate details (BOM Number, Item Number, Count)
  
  GET full record details for all duplicate combinations
  EXPORT full records to 'Duplicate_BOM_Items.xlsx'
  DISPLAY export confirmation message
ELSE:
  DISPLAY "No duplicates found!"
```

**Pass Criteria:** Zero duplicates found  
**Action if Failed:** Send duplicate list to ECC team for correction, or manually renumber in extracted file

### Validation 1.5: BOM Circular Reference Check

**Objective:** Detect circular references (material used in its own BOM)

**Method 1: Using Excel**

1. Create a combined view with both headers and items
2. Add column "Is_Circular" with formula:

```excel
=IF(A2=F2, "CIRCULAR REFERENCE", "OK")
```
Where A2 = Parent Material, F2 = Component Material

3. Filter to show "CIRCULAR REFERENCE"

**Method 2: Using Python (Pseudo Code)**

```
LOAD 'BOM_Headers_Extract_[DATE].xlsx' into headers dataframe
LOAD 'BOM_Items_Extract_[DATE].xlsx' into items dataframe

JOIN items WITH headers ON 'BOM Number':
  BRING in 'Material' field from headers
  RENAME it to 'Parent Material'

CHECK for circular references:
  FIND all rows WHERE Parent Material = Component
  STORE results in circular dataframe

DISPLAY "Circular references found: [count]"

IF circular references found:
  DISPLAY details: Parent Material, Component, BOM Number, Item Number
  EXPORT to 'Circular_References.xlsx'
  DISPLAY export confirmation
ELSE:
  DISPLAY "No circular references found!"
```

**Pass Criteria:** Zero circular references found  
**Action if Failed:** Send list to ECC team for review, or document as acceptable if business requires it

### Validation 1.6: Overall Extracted Data Quality Report

**Objective:** Generate a summary report of all validation checks

**Python Script - Comprehensive Validation (Pseudo Code)**

```
DISPLAY report header with title and current date/time

LOAD 'BOM_Headers_Extract_[DATE].xlsx' into headers dataframe
LOAD 'BOM_Items_Extract_[DATE].xlsx' into items dataframe

INITIALIZE validation_results as empty list

VALIDATION CHECK 1: Header Data Quality
  COUNT headers WHERE Base Quantity is NULL OR <= 0
  COUNT headers WHERE Base Unit is NULL OR empty
  ADD results to validation_results with PASS/FAIL status

VALIDATION CHECK 2: Item Data Quality
  COUNT items WHERE Component is NULL OR empty
  COUNT items WHERE Quantity is NULL OR <= 0
  COUNT items WHERE Unit is NULL OR empty
  ADD results to validation_results with PASS/FAIL status

VALIDATION CHECK 3: Duplicate Item Numbers
  GROUP items BY (BOM Number, Item Number) and COUNT occurrences
  COUNT groups WHERE count > 1
  ADD result to validation_results with PASS/FAIL status

VALIDATION CHECK 4: Circular References
  JOIN items with headers to get Parent Material
  COUNT records WHERE Parent Material = Component
  ADD result to validation_results with PASS/FAIL status

DISPLAY section "VALIDATION RESULTS"
  DISPLAY validation_results table with columns: Check, Issues Found, Status

DISPLAY section "SUMMARY STATISTICS"
  DISPLAY total BOM headers count
  DISPLAY total BOM items count
  DISPLAY unique parent materials count
  DISPLAY unique component materials count
  CALCULATE and DISPLAY average items per BOM

CALCULATE total issues across all checks
DISPLAY "OVERALL ASSESSMENT":
  IF total issues = 0:
    DISPLAY "PASS - Ready for Migration"
  ELSE:
    DISPLAY "FAIL - Issues Must Be Resolved"
  DISPLAY total issues count

EXPORT validation_results to 'BOM_Validation_Report.xlsx'
DISPLAY save confirmation message
```

**Pass Criteria:** All validation checks show "PASS" status  
**Action if Failed:** Address all issues before proceeding to template creation

---

## Stage 2: Template Validation (Pre-Import)

### Validation 2.1: Template Structure Check

**Objective:** Verify template has required columns and format

**Manual Checklist:**
- [ ] Excel file opens without errors
- [ ] Sheet names match expected structure (BOM_Header, BOM_Items)
- [ ] Column headers match template specification exactly
- [ ] No extra columns inserted
- [ ] No empty rows between data records
- [ ] File is saved in correct format (CSV UTF-8 or XLSX)

### Validation 2.2: Required Fields Populated

**Objective:** Ensure all mandatory fields have values

**Excel Formula (apply to each row):**

For BOM Header:
```
=IF(OR(ISBLANK(Material), ISBLANK(Plant), ISBLANK(BOMUsage), ISBLANK(BOMHeaderBaseUnit), ISBLANK(BOMHeaderQuantity)), "MISSING REQUIRED FIELD", "OK")
```

For BOM Items:
```
=IF(OR(ISBLANK(Material), ISBLANK(Plant), ISBLANK(BOMUsage), ISBLANK(BOMItemNumber), ISBLANK(BOMItemComponent), ISBLANK(BOMItemQuantity), ISBLANK(BOMItemUnit)), "MISSING REQUIRED FIELD", "OK")
```

**Pass Criteria:** All cells show "OK"  
**Action if Failed:** Populate missing required fields

### Validation 2.3: Data Format Validation

**Objective:** Verify data formats are correct

**Validation Rules:**

```
Material Number:
- Length: 1-40 characters
- No leading zeros
- Alphanumeric only
- Formula: =IF(AND(LEN(A2)>0, LEN(A2)<=40, ISNUMBER(--A2)=FALSE), "OK", "INVALID FORMAT")

Quantity Fields:
- Numeric with decimals
- Greater than zero
- Formula: =IF(AND(ISNUMBER(F2), F2>0), "OK", "INVALID QUANTITY")

Date Fields:
- Format: YYYY-MM-DD
- Valid date range
- Formula: =IF(OR(G2="", AND(LEN(G2)=10, ISNUMBER(DATEVALUE(G2)))), "OK", "INVALID DATE")

Item Number:
- Exactly 4 digits
- Format: 0010, 0020, etc.
- Formula: =IF(AND(LEN(E2)=4, ISNUMBER(--E2)), "OK", "INVALID ITEM NUMBER")
```

### Validation 2.4: Business Logic Validation

**Objective:** Verify data meets business rules

```sql
-- In Excel or database, check these rules:

-- Rule 1: BOM Header and Items match
SELECT DISTINCT Material, Plant, BOMUsage, AlternativeBOM 
FROM BOM_Items
WHERE NOT EXISTS (
    SELECT 1 FROM BOM_Header h
    WHERE h.Material = BOM_Items.Material
    AND h.Plant = BOM_Items.Plant
    AND h.BOMUsage = BOM_Items.BOMUsage
    AND h.AlternativeBOM = BOM_Items.AlternativeBOM
);

-- Rule 2: No duplicate item numbers within same BOM
SELECT Material, Plant, BOMUsage, AlternativeBOM, BOMItemNumber, COUNT(*)
FROM BOM_Items
GROUP BY Material, Plant, BOMUsage, AlternativeBOM, BOMItemNumber
HAVING COUNT(*) > 1;

-- Rule 3: Component quantities are positive
SELECT Material, BOMItemNumber, BOMItemComponent, BOMItemQuantity
FROM BOM_Items
WHERE BOMItemQuantity <= 0;
```

**Pass Criteria:** All queries return zero records  
**Action if Failed:** Fix data inconsistencies in template

### Validation 2.5: Record Count Validation

**Objective:** Verify expected number of records

```
Expected Counts (from extraction):
- BOM Headers: [____]
- BOM Items: [____]
- Unique Parent Materials: [____]
- Unique Components: [____]

Template Counts:
- BOM Headers: =COUNTA(A2:A9999)-COUNTBLANK(A2:A9999)
- BOM Items: =COUNTA(A2:A9999)-COUNTBLANK(A2:A9999)
- Unique Parent Materials: =SUMPRODUCT(1/COUNTIF(A2:A9999,A2:A9999))
- Unique Components: =SUMPRODUCT(1/COUNTIF(F2:F9999,F2:F9999))
```

**Pass Criteria:** Template counts match expected counts (±5 tolerance for data cleansing)  
**Action if Failed:** Investigate missing records

---

## Stage 3: Post-Import Validation (Public Cloud Target)

### Validation 3.1: Import Success Confirmation

**Objective:** Verify all records imported successfully

**Check import log/monitor:**
- [ ] Import job completed without errors
- [ ] Number of records processed matches template count
- [ ] Zero records rejected
- [ ] All error messages reviewed and resolved

**If available, query target system:**

```sql
-- Count imported BOMs (pseudo-code, adjust for Public Cloud API)
SELECT COUNT(*) FROM BillOfMaterial 
WHERE CreatedDate = [import_date];
```

### Validation 3.2: BOM Header Reconciliation

**Objective:** Verify all BOM headers exist in target system

```sql
-- Compare source vs target counts by material
-- Source (ECC):
SELECT 
    MATNR as "Material",
    WERKS as "Plant",
    COUNT(DISTINCT STLNR) as "BOM Count"
FROM MAST
WHERE STLAN = '1'
GROUP BY MATNR, WERKS
ORDER BY MATNR, WERKS;

-- Target (Public Cloud): Run equivalent query
-- Then compare results
```

**Pass Criteria:** Counts match exactly  
**Action if Failed:** Identify and re-import missing BOMs

### Validation 3.3: BOM Item Reconciliation

**Objective:** Verify all BOM items exist with correct data

```sql
-- Source (ECC) - Item counts per BOM
SELECT 
    m.MATNR as "Material",
    m.WERKS as "Plant",
    COUNT(sp.POSNR) as "Item Count",
    SUM(sp.MENGE) as "Total Quantity"
FROM 
    MAST m
    INNER JOIN STPO sp ON m.STLNR = sp.STLNR
WHERE 
    m.STLAN = '1'
    AND sp.LOEKZ = ''
GROUP BY 
    m.MATNR, m.WERKS
ORDER BY 
    m.MATNR, m.WERKS;

-- Target (Public Cloud): Run equivalent query
-- Compare results
```

**Pass Criteria:** Item counts and total quantities match  
**Action if Failed:** Identify and re-import missing items

### Validation 3.4: BOM Structure Integrity

**Objective:** Verify parent-child relationships are correct

**Sample BOMs to test (select 10-20 representative BOMs):**
- Simple BOMs (1-5 items)
- Complex BOMs (20+ items)
- Multi-level BOMs (components that are also parents)

**For each sample:**
1. Print/export BOM from ECC (transaction CS03)
2. Print/export BOM from Public Cloud
3. Compare side-by-side:
   - [ ] All components present
   - [ ] Quantities match
   - [ ] Units match
   - [ ] Item numbers match
   - [ ] Item sequence correct

**Pass Criteria:** 100% match on all sampled BOMs  
**Action if Failed:** Investigate mapping errors and re-import affected BOMs

### Validation 3.5: Field-Level Data Accuracy

**Objective:** Verify specific field values migrated correctly

**Random sample validation (50-100 records):**

```sql
-- Source data sample
SELECT 
    m.MATNR,
    m.WERKS,
    sp.POSNR,
    sp.IDNRK,
    sp.MENGE,
    sp.MEINS,
    sp.AUSCH as "Scrap_Percent"
FROM MAST m
INNER JOIN STPO sp ON m.STLNR = sp.STLNR
WHERE m.MATNR IN ('Material1', 'Material2', 'Material3')
ORDER BY m.MATNR, sp.POSNR;

-- Target data sample (run equivalent query)
-- Compare field by field
```

**Pass Criteria:** 95%+ accuracy across all fields  
**Action if Failed:** Review transformation logic and re-import

---

## Stage 4: Reconciliation and Final Checks

### Reconciliation 4.1: Volume Reconciliation

**Objective:** Confirm total volumes match

| Metric | Source (ECC) | Template | Target (Public Cloud) | Variance | Status |
|--------|--------------|----------|----------------------|----------|--------|
| Total BOM Headers | _____ | _____ | _____ | _____ | [ ] |
| Total BOM Items | _____ | _____ | _____ | _____ | [ ] |
| Unique Parent Materials | _____ | _____ | _____ | _____ | [ ] |
| Unique Component Materials | _____ | _____ | _____ | _____ | [ ] |
| Average Items per BOM | _____ | _____ | _____ | _____ | [ ] |

**Pass Criteria:** Variance < 1% for all metrics  
**Action if Failed:** Perform detailed record-by-record comparison

### Reconciliation 4.2: Critical BOMs Validation

**Objective:** Verify most important BOMs migrated correctly

**Identify critical BOMs:**
- High-volume products
- Revenue-generating products
- Complex assemblies
- Recently changed BOMs

**For each critical BOM:**
- [ ] BOM exists in target
- [ ] All items present
- [ ] Quantities correct
- [ ] Can be used in production order (if applicable)
- [ ] Print/report output matches source

### Reconciliation 4.3: Multi-Level BOM Testing

**Objective:** Verify multi-level BOM structures are intact

**Test Cases:**
1. Select 5 top-level assemblies
2. For each, generate full exploded BOM (all levels)
3. Compare source vs target:
   - [ ] Same number of levels
   - [ ] All components at all levels present
   - [ ] Total quantities calculated correctly
   - [ ] No circular references

### Reconciliation 4.4: User Acceptance Testing

**Objective:** End users verify BOMs are usable

**Test Activities:**
- [ ] Users can search and display BOMs
- [ ] BOM reports generate correctly
- [ ] BOMs can be used in production planning
- [ ] BOMs can be used in costing
- [ ] Changes can be made to BOMs (if applicable in test)

**Pass Criteria:** All test activities completed successfully  
**Action if Failed:** Document issues and plan corrective actions

---

## Error Scenarios and Fixes

### Error Scenario 1: Import Fails - Missing Material
**Error:** "Component material XYZ does not exist"  
**Root Cause:** Component not created in target system  
**Fix:** Create material master for XYZ, then re-import BOM

### Error Scenario 2: Import Fails - Invalid UOM
**Error:** "Unit of measure ABC not found"  
**Root Cause:** UOM not configured in target system  
**Fix:** Configure UOM or map to equivalent unit, update template, re-import

### Error Scenario 3: Import Succeeds but Data Missing
**Error:** BOM created but some items missing  
**Root Cause:** Items filtered out due to validation rules  
**Fix:** Review import log, correct item data, re-import missing items

### Error Scenario 4: Quantity Mismatch
**Error:** Imported quantity differs from source  
**Root Cause:** Decimal rounding or conversion error  
**Fix:** Adjust transformation logic, re-import with correct quantities

### Error Scenario 5: Duplicate BOM Created
**Error:** Multiple BOMs exist for same material/plant  
**Root Cause:** Alternative BOM not specified or duplicated  
**Fix:** Delete duplicate, ensure Alternative BOM field populated correctly

---

## Validation Checklist Summary

**Pre-Extraction (ECC):**
- [ ] BOM header data quality validated
- [ ] BOM item data quality validated
- [ ] All component materials exist
- [ ] No duplicate item numbers
- [ ] No circular references
- [ ] Record counts documented

**Template Validation:**
- [ ] Template structure correct
- [ ] Required fields populated
- [ ] Data formats valid
- [ ] Business logic rules passed
- [ ] Record counts match extraction

**Post-Import (Public Cloud):**
- [ ] Import job completed successfully
- [ ] BOM headers reconciled
- [ ] BOM items reconciled
- [ ] Structure integrity verified
- [ ] Field-level accuracy confirmed

**Final Reconciliation:**
- [ ] Volume reconciliation complete
- [ ] Critical BOMs validated
- [ ] Multi-level BOMs tested
- [ ] User acceptance testing passed

---

## Validation Tools and Scripts

### Excel Validation Template

Create an Excel file with these validation formulas:

**Sheet: Validation_Summary**
```
| Check Name | Formula | Status | Count |
|------------|---------|--------|-------|
| Missing Required Fields | =COUNTIF(BOM_Items!Z:Z,"MISSING REQUIRED FIELD") | | |
| Invalid Quantities | =COUNTIF(BOM_Items!AA:AA,"INVALID QUANTITY") | | |
| Invalid Dates | =COUNTIF(BOM_Header!AB:AB,"INVALID DATE") | | |
```

### Python Validation Script (Optional - Pseudo Code)

```
LOAD 'BOM_Template.xlsx' sheet 'BOM_Header' into bom_header dataframe
LOAD 'BOM_Template.xlsx' sheet 'BOM_Items' into bom_items dataframe

VALIDATION 1: Required fields check
  DEFINE required_header_fields = [Material, Plant, BOMUsage, BOMHeaderBaseUnit, BOMHeaderQuantity]
  FOR EACH required field:
    COUNT NULL values in bom_header
    IF count > 0: DISPLAY field name and count
  
  DEFINE required_item_fields = [Material, Plant, BOMUsage, BOMItemNumber, BOMItemComponent, BOMItemQuantity, BOMItemUnit]
  FOR EACH required field:
    COUNT NULL values in bom_items
    IF count > 0: DISPLAY field name and count

VALIDATION 2: Positive quantities
  FIND all bom_items WHERE BOMItemQuantity <= 0
  DISPLAY "Invalid Quantities (<=0): [count] records"

VALIDATION 3: Duplicate item numbers
  GROUP bom_items BY (Material, Plant, BOMUsage, AlternativeBOM, BOMItemNumber)
  COUNT occurrences of each group
  KEEP only groups WHERE count > 1
  DISPLAY "Duplicate Item Numbers: [count] instances"

VALIDATION 4: Orphan items (items without matching header)
  LEFT JOIN bom_items with bom_header ON (Material, Plant, BOMUsage, AlternativeBOM)
  FIND all items WHERE no matching header found
  DISPLAY "Orphan Items (no header): [count] records"

DISPLAY "Validation Complete!"
```

---

## Notes

- Perform validations in sequence - don't skip stages
- Document all validation results
- Keep validation reports for audit purposes
- Re-run validations after any data corrections
- Plan for 2-3 validation cycles in project timeline

