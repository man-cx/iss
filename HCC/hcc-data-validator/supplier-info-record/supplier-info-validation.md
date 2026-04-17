# Supplier Info Record Validation Procedures

## Overview
This document provides comprehensive validation procedures, validation logic, and pass/fail criteria for Supplier Info Record data migration at all stages.

**Important Note:** Since you don't have direct access to SAP ECC, Stage 1 validations work with extracted files provided by the ECC team rather than running SQL queries directly in the database. All validations use pseudo code and logic descriptions that you can implement using Python, pandas, or similar tools.

## Validation Stages

The validation process is divided into four stages:

1. **Stage 1:** Post-Extraction Validation (validate extracted files from ECC team)
2. **Stage 2:** Template Validation (in Excel before upload)
3. **Stage 3:** Post-Import Validation (in Public Cloud after upload)
4. **Stage 4:** Reconciliation (comparing source vs target)

---

## Required Files from ECC Team

Before starting Stage 1 validation, ensure you receive these files from the ECC extraction team:

### Core Files (Required)
- `SupplierInfo_Combined_YYYYMMDD.xlsx` - Combined info records (EINA + EINE data)
  - OR separate files:
    - `SupplierInfo_General_YYYYMMDD.xlsx` - General data (EINA)
    - `SupplierInfo_PurchOrg_YYYYMMDD.xlsx` - Purchasing org data (EINE)

### Master Data Files (Required for Validation 1.3)
- `Vendors_MasterData.xlsx` - All active vendors from LFA1 table
- `Materials_MasterData.xlsx` - All active materials from MARA table

### Configuration Files (Recommended)
- `PurchasingGroups_Master.xlsx` - Valid purchasing groups from T024 table
- `Plants_Master.xlsx` - Valid plants from T001W table
- `PurchasingOrgs_Master.xlsx` - Valid purchasing organizations

### Optional Files
- `SupplierInfo_Pricing_YYYYMMDD.xlsx` - Pricing conditions from A018/KONP (if using condition records)

**File Format Requirements:**
- Preferred format: XLSX (Excel) or CSV with UTF-8 encoding
- First row must contain column headers
- Date fields should be in YYYYMMDD or YYYY-MM-DD format
- No merged cells or formatting
- Column names should match the extraction queries in `supplier-info-extraction.md`

---

# Stage 1: Post-Extraction Validation (Extracted Files)

**Note:** Since you don't have direct access to ECC, another team will extract the data. These validations run on the extracted CSV/Excel files to identify and fix issues before transformation.

**Assumption:** The ECC team has provided you with extracted files containing supplier info record data.

## Validation 1.1: Info Record Header Data Quality

**Purpose:** Check for missing or invalid data in extracted general data file (from EINA table).

**Input File:** `SupplierInfo_General_YYYYMMDD.xlsx` or `SupplierInfo_Combined_YYYYMMDD.xlsx`

**Validation Logic (Pseudo Code):**
```
FOR EACH row in extracted_file:
    // Check for missing vendor
    IF row.vendor_number is NULL or EMPTY or BLANK:
        ADD to issues_list: "Missing Vendor" for row number
        INCREMENT missing_vendor_count
    
    // Check for missing material
    IF row.material_number is NULL or EMPTY or BLANK:
        ADD to issues_list: "Missing Material" for row number
        INCREMENT missing_material_count
    
    // Check for invalid order unit
    IF row.order_unit is NULL or EMPTY or BLANK:
        ADD to issues_list: "Invalid Order Unit" for row number
        INCREMENT invalid_unit_count

// Generate validation report
REPORT validation_results:
    - Missing Vendor: missing_vendor_count records
    - Missing Material: missing_material_count records
    - Invalid Order Unit: invalid_unit_count records
    - List of affected row numbers

SAVE issues_list to: "Pre_Extraction_Issues.xlsx"
```

**Implementation Notes:**
- Use pandas (Python) or similar tool to read CSV/Excel file
- Check for NULL, empty string, whitespace-only values
- Record row numbers for troubleshooting
- Create detailed issue report with specific rows affected

**Pass Criteria:**
- All counts should be 0
- If > 0, document and send back to ECC team for correction

**Fail Actions:**
- Document all records with issues (row numbers, vendor, material)
- Contact ECC extraction team to fix and re-extract
- Consider excluding problematic records from migration if cannot be fixed

---

## Validation 1.2: Purchasing Organization Data Quality

**Purpose:** Check for issues in purchasing organization data (from EINE table).

**Input File:** `SupplierInfo_PurchOrg_YYYYMMDD.xlsx` or `SupplierInfo_Combined_YYYYMMDD.xlsx`

**Validation Logic (Pseudo Code):**
```
INITIALIZE counters:
    missing_purch_org_count = 0
    zero_negative_price_count = 0
    missing_currency_count = 0
    missing_price_unit_count = 0

FOR EACH row in extracted_file:
    // Check for missing purchasing organization
    IF row.purchasing_org is NULL or EMPTY:
        ADD to issues: "Missing Purchasing Org" for row
        INCREMENT missing_purch_org_count
    
    // Check for zero or negative prices
    IF row.net_price <= 0:
        ADD to issues: "Zero or Negative Price" for row
        INCREMENT zero_negative_price_count
        STORE row details for business review
    
    // Check for missing currency when price exists
    IF (row.currency is NULL or EMPTY) AND row.net_price > 0:
        ADD to issues: "Missing Currency" for row
        INCREMENT missing_currency_count
        MARK as CRITICAL error
    
    // Check for missing price unit when price exists
    IF (row.price_unit is NULL or 0) AND row.net_price > 0:
        ADD to issues: "Missing Price Unit" for row
        INCREMENT missing_price_unit_count

// Generate validation report
REPORT validation_results:
    - Missing Purchasing Org: missing_purch_org_count records
    - Zero or Negative Price: zero_negative_price_count records (needs business review)
    - Missing Currency: missing_currency_count records (CRITICAL)
    - Missing Price Unit: missing_price_unit_count records

SAVE detailed_issues to: "PurchOrg_Validation_Issues.xlsx"
```

**Implementation Notes:**
- Zero prices need special handling - document separately for business approval
- Missing currency with valid price is CRITICAL - must be fixed
- Missing price unit can default to 1 during transformation

**Pass Criteria:**
- All counts should be 0 for "Missing" validations (except zero prices with approval)
- Zero prices may be acceptable if documented (consignment, etc.)
- Missing currency with price > 0 is critical error - MUST be 0

**Fail Actions:**
- Send critical errors (missing currency) back to ECC team
- Document zero prices and get business approval before proceeding
- Missing price units can be defaulted to 1 during transformation

---

## Validation 1.3: Vendor and Material Existence

**Purpose:** Ensure all referenced vendors and materials exist in the extracted master data files.

**Input Files:** 
- `SupplierInfo_Combined_YYYYMMDD.xlsx` (info records)
- `Vendors_MasterData.xlsx` (vendor master - from ECC team)
- `Materials_MasterData.xlsx` (material master - from ECC team)

**Validation Logic (Pseudo Code):**
```
// Load master data into memory for fast lookup
vendor_master_list = LOAD_UNIQUE_VALUES from "Vendors_MasterData.xlsx" column: vendor_number
material_master_list = LOAD_UNIQUE_VALUES from "Materials_MasterData.xlsx" column: material_number

INITIALIZE:
    vendors_not_exist = []
    materials_not_exist = []

FOR EACH row in info_records_file:
    // Check if vendor exists in vendor master
    IF row.vendor_number NOT IN vendor_master_list:
        ADD to vendors_not_exist: {
            info_record: row.info_record_number,
            vendor: row.vendor_number,
            material: row.material_number
        }
    
    // Check if material exists in material master
    IF row.material_number NOT IN material_master_list:
        ADD to materials_not_exist: {
            info_record: row.info_record_number,
            vendor: row.vendor_number,
            material: row.material_number
        }

// Generate validation report
REPORT validation_results:
    - Vendors Not in Master: LENGTH(vendors_not_exist)
    - Materials Not in Master: LENGTH(materials_not_exist)
    - Detailed list saved to file

SAVE vendors_not_exist to: "Missing_Vendors.xlsx"
SAVE materials_not_exist to: "Missing_Materials.xlsx"

IF LENGTH(vendors_not_exist) > 0 OR LENGTH(materials_not_exist) > 0:
    ALERT: "CRITICAL - Master data missing!"
```

**Implementation Notes:**
- Use sets or dictionaries for fast lookup of master data
- Remove leading zeros consistently when comparing vendor/material numbers
- This is a CRITICAL validation - cannot proceed without clean master data

**Pass Criteria:**
- No records returned (count = 0 for both vendors and materials)
- All vendors and materials in info records exist in master data files

**Fail Actions:**
- CRITICAL error - STOP migration
- Request complete vendor master extract from ECC team
- Request complete material master extract from ECC team
- Alternative: Remove info records with missing master data from scope

---

## Validation 1.4: Orphaned Purchasing Org Records

**Purpose:** Find purchasing org records (EINE) without corresponding general records (EINA).

**Input Files:** 
- `SupplierInfo_General_YYYYMMDD.xlsx` (EINA data)
- `SupplierInfo_PurchOrg_YYYYMMDD.xlsx` (EINE data)

**Note:** If using combined file, this validation may not be needed.

**Validation Logic (Pseudo Code):**
```
// Load general info record numbers into a set
general_info_records = LOAD_UNIQUE_VALUES from "SupplierInfo_General_YYYYMMDD.xlsx" column: info_record_number

INITIALIZE:
    orphaned_records = []

// Check each purchasing org record
FOR EACH row in "SupplierInfo_PurchOrg_YYYYMMDD.xlsx":
    IF row.info_record_number NOT IN general_info_records:
        ADD to orphaned_records: {
            info_record_number: row.info_record_number,
            purchasing_org: row.purchasing_org,
            plant: row.plant
        }

// Generate validation report
REPORT validation_results:
    - Orphaned EINE records: LENGTH(orphaned_records)
    - These records have purchasing data but no general data

SAVE orphaned_records to: "Orphaned_PurchOrg_Records.xlsx"

IF LENGTH(orphaned_records) > 0:
    ALERT: "Data integrity issue - orphaned purchasing org records found!"
```

**Implementation Notes:**
- This indicates data integrity issues in source ECC system
- Use set lookup for performance with large datasets
- If using combined extraction, this issue would be caught automatically

**Pass Criteria:**
- No records returned (count = 0)
- All purchasing org records have corresponding general records

**Fail Actions:**
- Data integrity issue - contact ECC extraction team
- Request re-extraction with proper joins
- Alternative: Exclude orphaned records from migration

---

## Validation 1.5: Duplicate Info Records

**Purpose:** Identify potential duplicates (same vendor-material-org-plant combination).

**Input File:** `SupplierInfo_Combined_YYYYMMDD.xlsx`

**Validation Logic (Pseudo Code):**
```
// Create a dictionary to track combinations
combination_tracker = {}

FOR EACH row in info_records_file:
    // Create unique key from vendor + material + org + plant
    key = CONCATENATE(
        row.vendor_number, 
        "|", 
        row.material_number, 
        "|", 
        row.purchasing_org, 
        "|", 
        row.plant
    )
    
    // Track occurrences
    IF key EXISTS in combination_tracker:
        combination_tracker[key].count += 1
        combination_tracker[key].info_records.APPEND(row.info_record_number)
    ELSE:
        combination_tracker[key] = {
            vendor: row.vendor_number,
            material: row.material_number,
            purchasing_org: row.purchasing_org,
            plant: row.plant,
            count: 1,
            info_records: [row.info_record_number]
        }

// Find duplicates (count > 1)
duplicates = []
FOR EACH key, data in combination_tracker:
    IF data.count > 1:
        ADD data to duplicates
        SORT data.info_records  // First = oldest, Last = newest

// Generate validation report
REPORT validation_results:
    - Duplicate combinations found: LENGTH(duplicates)
    - Sort by count (highest duplicates first)

SAVE duplicates to: "Duplicate_InfoRecords.xlsx" with columns:
    - Vendor, Material, Purchasing Org, Plant
    - Duplicate Count
    - Info Record Numbers (all occurrences)
    - Recommendation: Keep newest, review with business
```

**Implementation Notes:**
- Duplicates may be intentional (different info record categories, sub-ranges)
- Handle blank plants as separate category (plant-specific vs non-plant-specific)
- Sort duplicates by count to prioritize review

**Pass Criteria:**
- No records returned, OR
- Duplicates are intentional (different info record categories or sub-ranges)
- All duplicates reviewed and documented

**Fail Actions:**
- Review each duplicate with business team
- Decide which record to keep (usually most recent)
- Flag others for exclusion from migration
- Document decision in: "Duplicate_Resolution_Decisions.xlsx"

---

## Validation 1.6: Invalid Purchasing Groups

**Purpose:** Check for purchasing groups that may not exist in Public Cloud.

**Input Files:** 
- `SupplierInfo_Combined_YYYYMMDD.xlsx` (info records)
- `PurchasingGroups_Master.xlsx` (purchasing group master - from ECC team or Public Cloud)

**Validation Logic (Pseudo Code):**
```
// Load valid purchasing groups
valid_purchasing_groups = LOAD_UNIQUE_VALUES from "PurchasingGroups_Master.xlsx" column: purchasing_group

// Track invalid purchasing groups
invalid_purch_groups = {}

FOR EACH row in info_records_file:
    IF row.purchasing_group is NOT NULL AND row.purchasing_group is NOT EMPTY:
        IF row.purchasing_group NOT IN valid_purchasing_groups:
            // Track this purchasing group
            IF row.purchasing_group NOT IN invalid_purch_groups:
                invalid_purch_groups[row.purchasing_group] = {
                    purch_group: row.purchasing_group,
                    count: 0,
                    sample_vendor: row.vendor_number,
                    sample_material: row.material_number
                }
            invalid_purch_groups[row.purchasing_group].count += 1

// Generate validation report
REPORT validation_results:
    - Invalid purchasing groups: LENGTH(invalid_purch_groups)
    - Total affected info records: SUM of all counts

SAVE invalid_purch_groups to: "Invalid_PurchasingGroups.xlsx"
```

**Implementation Notes:**
- Purchasing groups should be configured in Public Cloud before migration
- If list not available, extract unique purchasing groups and send to Public Cloud team
- Missing purchasing groups can be cleared if not critical

**Pass Criteria:**
- No invalid purchasing groups (count = 0), OR
- All purchasing groups confirmed to exist in Public Cloud

**Fail Actions:**
- Send list of purchasing groups to Public Cloud team
- Ensure all groups are created in Public Cloud before migration, OR
- Clear purchasing group field for affected info records if not critical

---

## Validation 1.7: Tax Codes Inventory

**Purpose:** Identify all tax codes used in info records for Public Cloud configuration.

**Input File:** `SupplierInfo_Combined_YYYYMMDD.xlsx`

**Validation Logic (Pseudo Code):**
```
// Track all tax codes used
tax_codes_summary = {}

FOR EACH row in info_records_file:
    IF row.tax_code is NOT NULL AND row.tax_code is NOT EMPTY:
        IF row.tax_code NOT IN tax_codes_summary:
            tax_codes_summary[row.tax_code] = {
                tax_code: row.tax_code,
                count: 0,
                sample_vendor: row.vendor_number,
                sample_material: row.material_number
            }
        tax_codes_summary[row.tax_code].count += 1

// Sort by frequency (most used first)
SORT tax_codes_summary BY count DESCENDING

// Generate validation report
REPORT validation_results:
    - Unique tax codes found: LENGTH(tax_codes_summary)
    - Total info records with tax codes: SUM of all counts
    - List of all tax codes with usage count

SAVE tax_codes_summary to: "TaxCodes_Inventory.xlsx"

// Create mapping template for Public Cloud team
CREATE mapping_template with columns:
    - ECC_Tax_Code
    - Usage_Count
    - Public_Cloud_Tax_Code (empty - to be filled)
    - Exists_In_Public_Cloud (Yes/No - to be verified)
    - Notes
```

**Implementation Notes:**
- Tax codes are country/region specific
- Work with tax/finance team to create ECC to Public Cloud mapping
- Some tax codes may need different codes in Public Cloud

**Pass Criteria:**
- All tax codes documented and inventory created
- Mapping to Public Cloud tax codes confirmed
- All codes will be configured in Public Cloud before migration

**Fail Actions:**
- Create mapping table for tax codes
- Send inventory to Public Cloud team for configuration
- Work with tax team to map ECC codes to Public Cloud codes if different

---

## Validation 1.8: Price Date Issues

**Purpose:** Find outdated or future prices that may need review.

**Input File:** `SupplierInfo_Combined_YYYYMMDD.xlsx`

**Validation Logic (Pseudo Code):**
```
IMPORT datetime library
today = CURRENT_DATE
two_years_ago = today - 24 MONTHS

INITIALIZE:
    expired_prices = []
    future_prices = []

FOR EACH row in info_records_file:
    IF row.net_price > 0 AND row.price_date is NOT NULL:
        // Convert price_date to date object (format: YYYYMMDD or YYYY-MM-DD)
        price_date = PARSE_DATE(row.price_date)
        
        // Check for expired prices (> 2 years old)
        IF price_date < two_years_ago:
            ADD to expired_prices: {
                info_record: row.info_record_number,
                vendor: row.vendor_number,
                material: row.material_number,
                price: row.net_price,
                price_date: price_date,
                age_in_days: today - price_date
            }
        
        // Check for future prices
        IF price_date > today:
            ADD to future_prices: {
                info_record: row.info_record_number,
                vendor: row.vendor_number,
                material: row.material_number,
                price: row.net_price,
                price_date: price_date,
                days_in_future: price_date - today
            }

// Generate validation report
REPORT validation_results:
    - Expired prices (> 2 years old): LENGTH(expired_prices)
    - Future price dates: LENGTH(future_prices)

SAVE expired_prices to: "Expired_Prices_For_Review.xlsx"
SAVE future_prices to: "Future_Prices_For_Review.xlsx"

// Categorize expired prices by age
age_distribution = CATEGORIZE expired_prices BY:
    - 2-3 years old
    - 3-5 years old
    - > 5 years old
```

**Implementation Notes:**
- Handle different date formats (YYYYMMDD from ECC, YYYY-MM-DD, etc.)
- Expired prices may still be valid (no price changes in years)
- Future prices may be intentional (pre-negotiated rates)

**Pass Criteria:**
- Expired prices: Accept with business approval
- Future prices: Review and determine if intentional
- Document all findings for business review

**Fail Actions:**
- Send expired prices list to purchasing team for review
- Get business approval for migration of old prices
- Verify future price dates are intentional (not data errors)

---

## Validation 1.9: Tolerance and Quantity Settings

**Purpose:** Verify delivery tolerances and order quantities are reasonable.

**Input File:** `SupplierInfo_Combined_YYYYMMDD.xlsx`

**Validation Logic (Pseudo Code):**
```
INITIALIZE:
    overdelivery_issues = []
    underdelivery_issues = []
    minmax_qty_issues = []

FOR EACH row in info_records_file:
    // Check over-delivery tolerance > 100%
    IF row.overdelivery_tolerance is NOT NULL:
        IF row.overdelivery_tolerance > 100:
            ADD to overdelivery_issues: {
                info_record: row.info_record_number,
                vendor: row.vendor_number,
                material: row.material_number,
                tolerance: row.overdelivery_tolerance
            }
    
    // Check under-delivery tolerance > 100%
    IF row.underdelivery_tolerance is NOT NULL:
        IF row.underdelivery_tolerance > 100:
            ADD to underdelivery_issues: {
                info_record: row.info_record_number,
                vendor: row.vendor_number,
                material: row.material_number,
                tolerance: row.underdelivery_tolerance
            }
    
    // Check max order quantity < min order quantity
    IF row.max_order_qty is NOT NULL AND row.min_order_qty is NOT NULL:
        IF row.max_order_qty > 0 AND row.min_order_qty > 0:
            IF row.max_order_qty < row.min_order_qty:
                ADD to minmax_qty_issues: {
                    info_record: row.info_record_number,
                    vendor: row.vendor_number,
                    material: row.material_number,
                    min_qty: row.min_order_qty,
                    max_qty: row.max_order_qty
                }

// Generate validation report
REPORT validation_results:
    - Over-delivery tolerance > 100%: LENGTH(overdelivery_issues)
    - Under-delivery tolerance > 100%: LENGTH(underdelivery_issues)
    - Max Order Qty < Min Order Qty: LENGTH(minmax_qty_issues)

SAVE overdelivery_issues to: "Overdelivery_Tolerance_Issues.xlsx"
SAVE underdelivery_issues to: "Underdelivery_Tolerance_Issues.xlsx"
SAVE minmax_qty_issues to: "MinMax_Quantity_Issues.xlsx"
```

**Implementation Notes:**
- Tolerances > 100% are unusual but may be valid in some cases
- Min/Max quantity inversions are data errors and must be fixed
- Handle NULL values properly (missing tolerances are acceptable)

**Pass Criteria:**
- All counts should be 0, OR
- Issues are reviewed and approved by business

**Fail Actions:**
- Send tolerance issues to ECC team for correction
- Fix min/max order quantity inversions (CRITICAL)
- Document approved exceptions

---

## Stage 1 Summary Report

Generate overall summary statistics from the extracted files.

**Input File:** `SupplierInfo_Combined_YYYYMMDD.xlsx`

**Summary Logic (Pseudo Code):**
```
// Load the info records file
info_records = LOAD_FILE("SupplierInfo_Combined_YYYYMMDD.xlsx")

// Calculate summary statistics
summary_stats = {
    total_info_records: COUNT(info_records),
    
    unique_vendors: COUNT_DISTINCT(info_records, column: "vendor_number"),
    
    unique_materials: COUNT_DISTINCT(info_records, column: "material_number"),
    
    unique_purch_orgs: COUNT_DISTINCT(info_records, column: "purchasing_org"),
    
    unique_plants: COUNT_DISTINCT(info_records, column: "plant", exclude_blanks: TRUE),
    
    records_with_price: COUNT_WHERE(info_records, condition: "net_price > 0"),
    
    records_with_zero_price: COUNT_WHERE(info_records, condition: "net_price = 0"),
    
    records_with_plant: COUNT_WHERE(info_records, condition: "plant is NOT NULL AND plant != ''"),
    
    records_without_plant: COUNT_WHERE(info_records, condition: "plant is NULL OR plant = ''"),
    
    avg_price: AVERAGE(info_records, column: "net_price", where: "net_price > 0"),
    
    min_delivery_time: MINIMUM(info_records, column: "planned_delivery_time"),
    
    max_delivery_time: MAXIMUM(info_records, column: "planned_delivery_time"),
    
    avg_delivery_time: AVERAGE(info_records, column: "planned_delivery_time")
}

// Breakdown by purchasing organization
purch_org_breakdown = GROUP_BY(info_records, column: "purchasing_org") {
    purch_org: GROUP_KEY,
    count: COUNT_IN_GROUP,
    unique_vendors: COUNT_DISTINCT_IN_GROUP("vendor_number"),
    unique_materials: COUNT_DISTINCT_IN_GROUP("material_number")
}

// Generate comprehensive summary report
CREATE summary_report with:
    - Overall statistics (summary_stats)
    - Breakdown by purchasing organization (purch_org_breakdown)
    - Validation summary (counts from all validation checks 1.1-1.9)
    - Issues summary (total critical, high, medium, low issues)

SAVE summary_report to: "Stage1_Validation_Summary_Report.xlsx"

// Create executive summary (one-page view)
CREATE executive_summary:
    - Total Records: [count]
    - Critical Issues: [count] (MUST be 0 to proceed)
    - High Priority Issues: [count] (Should be < 5%)
    - Medium Priority Issues: [count] (Review recommended)
    - Status: [PASS / REVIEW NEEDED / FAIL]

DISPLAY executive_summary
```

**Pass Criteria for Stage 1:**
- All CRITICAL validation checks return 0 errors (missing master data, missing currencies, etc.)
- High priority errors < 5% of total records, OR
- All errors are documented and approved for migration by business team
- Summary report shows data is ready for transformation

**Fail Actions:**
- If critical errors exist, STOP and send back to ECC team
- Document all issues in detailed report
- Get business approval for non-critical issues before proceeding to Stage 2

---

# Stage 2: Template Validation (Excel File Before Upload)

Perform these validations on the prepared import template before uploading to Public Cloud.

## Validation 2.1: Required Fields Check

**Purpose:** Ensure all required fields are populated.

**Method:** Excel Formula

In a new column (e.g., Column AA), add this formula:

```excel
=IF(OR(ISBLANK(A2),ISBLANK(B2),ISBLANK(C2),ISBLANK(F2),ISBLANK(J2),ISBLANK(K2),ISBLANK(L2)),"MISSING REQUIRED","OK")
```

**Pass Criteria:**
- All rows show "OK"
- No "MISSING REQUIRED" values

**Fail Actions:**
- Filter for "MISSING REQUIRED"
- Fill in missing values or remove records
- Investigate why required fields are blank

---

## Validation 2.2: Data Format Check

**Purpose:** Verify data formats are correct.

### Check 1: Vendor and Material are Numeric

```excel
=IF(OR(NOT(ISNUMBER(VALUE(A2))),NOT(ISNUMBER(VALUE(B2)))),"FORMAT ERROR","OK")
```

### Check 2: Prices are Numeric and Positive

```excel
=IF(OR(NOT(ISNUMBER(J2)),J2<=0),"INVALID PRICE","OK")
```

### Check 3: Currency is 3 Characters

```excel
=IF(LEN(L2)<>3,"INVALID CURRENCY","OK")
```

### Check 4: Dates are Properly Formatted

```excel
=IF(AND(M2<>"",NOT(ISDATE(M2))),"INVALID DATE","OK")
```

**Pass Criteria:**
- All checks return "OK"

**Fail Actions:**
- Fix format errors
- Re-apply transformation rules from mapping document

---

## Validation 2.3: Duplicate Records Check

**Purpose:** Identify duplicate rows in template.

**Method:** Excel - Create Helper Column

```excel
=COUNTIFS($A$2:$A$10000,A2,$B$2:$B$10000,B2,$C$2:$C$10000,C2,$D$2:$D$10000,D2)
```

**Pass Criteria:**
- All values = 1 (no duplicates)

**Fail Actions:**
- Filter for values > 1
- Review duplicates with business team
- Keep most recent or accurate record
- Delete duplicates

---

## Validation 2.4: Referential Integrity (Vendor/Material Existence)

**Purpose:** Verify all vendors and materials exist in Public Cloud.

**Method:**
1. Export list of vendors from template (unique values)
2. Export list of materials from template (unique values)
3. Query Public Cloud for vendor master:
   ```sql
   SELECT PARTNER as "Vendor"
   FROM BusinessPartner
   WHERE PARTNER IN ([vendor list])
   ```
4. Query Public Cloud for material master:
   ```sql
   SELECT PRODUCT as "Material"
   FROM Product
   WHERE PRODUCT IN ([material list])
   ```

**Pass Criteria:**
- All vendors in template exist in Public Cloud vendor master
- All materials in template exist in Public Cloud material master

**Fail Actions:**
- Identify missing vendors/materials
- Migrate vendors/materials first (prerequisite)
- Remove info records with missing master data from template

---

## Validation 2.5: Business Logic Validation

**Purpose:** Check business rules and relationships.

### Check 1: Min ≤ Max Order Quantity

```excel
=IF(AND(O2<>"",P2<>"",VALUE(O2)>VALUE(P2)),"MIN > MAX","OK")
```

### Check 2: Price Unit is Valid

```excel
=IF(NOT(OR(K2=1,K2=10,K2=100,K2=1000)),"INVALID PRICE UNIT","OK")
```

### Check 3: Planned Delivery Time is Reasonable

```excel
=IF(H2>365,"DELIVERY TIME > 1 YEAR","OK")
```

**Pass Criteria:**
- All checks return "OK"

**Fail Actions:**
- Correct min/max quantities
- Set price unit to valid value (default: 1)
- Review and approve long delivery times

---

## Validation 2.6: Currency Code Validation

**Purpose:** Ensure all currency codes are valid ISO codes.

**Method:** Create a lookup table of valid currencies, then:

```excel
=IF(ISNA(VLOOKUP(L2,ValidCurrencies,1,FALSE)),"INVALID CURRENCY","OK")
```

**Valid Currency Examples:** USD, EUR, GBP, CAD, JPY, AUD, CHF, CNY, INR

**Pass Criteria:**
- All currencies return "OK"

**Fail Actions:**
- Correct invalid currency codes
- Map to valid ISO 4217 codes

---

## Validation 2.7: Unit of Measure Validation

**Purpose:** Verify all UoMs exist in Public Cloud.

**Method:** Similar to currency validation - create lookup table:

```excel
=IF(ISNA(VLOOKUP(F2,ValidUoMs,1,FALSE)),"INVALID UOM","OK")
```

**Pass Criteria:**
- All UoMs return "OK"

**Fail Actions:**
- Map to valid UoMs
- Create missing UoMs in Public Cloud before import

---

## Validation 2.8: Record Count Summary

**Purpose:** Verify template record counts match extraction.

**Method:** Compare these metrics:

| Metric | Extraction File | Template File | Variance | Status |
|--------|----------------|---------------|----------|--------|
| Total Records | [A] | [B] | [B-A] | [ ] |
| Unique Vendors | [C] | [D] | [D-C] | [ ] |
| Unique Materials | [E] | [F] | [F-E] | [ ] |

**Pass Criteria:**
- Variance ≤ 5% OR variance is explained

**Fail Actions:**
- Investigate significant variances
- Ensure no data loss during transformation
- Document intentional exclusions

---

## Stage 2 Validation Checklist

Before uploading template, confirm:

- [ ] All required fields populated
- [ ] No format errors
- [ ] No duplicate records
- [ ] All vendors exist in Public Cloud
- [ ] All materials exist in Public Cloud
- [ ] Business logic rules pass
- [ ] Currency codes valid
- [ ] Units of measure valid
- [ ] Record count reconciled with source
- [ ] File saved as CSV UTF-8 format

**Overall Pass Criteria:** All checklist items checked

---

# Stage 3: Post-Import Validation (Public Cloud After Upload)

Run these validations in SAP ERP Public Cloud after importing the template to verify data was imported correctly.

## Validation 3.1: Import Success Rate

**Purpose:** Check how many records imported successfully.

**Method:**
1. Review import log from Public Cloud data migration tool
2. Document:
   - Total records in template: ___________
   - Records imported successfully: ___________
   - Records failed: ___________
   - Success rate: ___________% 

**Pass Criteria:**
- Success rate ≥ 95%

**Fail Actions:**
- If < 95%, review error log in detail
- Fix errors and re-import failed records
- Document all errors and resolutions

---

## Validation 3.2: Record Count Verification

**Purpose:** Verify all expected records are in Public Cloud.

**Query (Public Cloud):**
```sql
-- Adjust table names based on your Public Cloud version
SELECT 
    COUNT(*) as "Total Supplier Info Records"
FROM 
    I_PurchasingInfoRecord
WHERE 
    IsDeleted = ''  -- or similar deletion flag
```

**Pass Criteria:**
- Count matches template record count (± 2%)

**Fail Actions:**
- Investigate missing records
- Re-import if necessary

---

## Validation 3.3: Price Accuracy Spot Check

**Purpose:** Verify prices imported correctly.

**Method:**
1. Select 20 random info records from template
2. Query Public Cloud for same records
3. Compare prices field by field

**Query (Public Cloud - example):**
```sql
SELECT 
    Supplier as "Vendor",
    Material,
    PurchasingOrganization,
    Plant,
    NetPriceAmount as "Price",
    Currency
FROM 
    I_PurchasingInfoRecord
WHERE 
    Supplier = '[vendor]'
    AND Material = '[material]'
    AND PurchasingOrganization = '[org]'
```

**Pass Criteria:**
- 100% of spot-checked records match exactly

**Fail Actions:**
- If mismatches found, expand spot check to larger sample
- Investigate transformation errors
- Re-import if systematic errors found

---

## Validation 3.4: Vendor-Material Relationships

**Purpose:** Verify all vendor-material combinations imported.

**Query (Public Cloud):**
```sql
SELECT 
    COUNT(DISTINCT Supplier) as "Unique Vendors",
    COUNT(DISTINCT Material) as "Unique Materials",
    COUNT(*) as "Total Info Records"
FROM 
    I_PurchasingInfoRecord
WHERE 
    IsDeleted = '';
```

**Pass Criteria:**
- Unique vendors matches expected count
- Unique materials matches expected count

**Fail Actions:**
- Identify missing vendors or materials
- Check if they were excluded during transformation
- Re-import if necessary

---

## Validation 3.5: Critical Info Records Verification

**Purpose:** Verify critical/high-value info records imported correctly.

**Method:**
1. Identify critical info records (provided by business):
   - High-volume materials
   - Strategic vendors
   - Critical for production
2. For each critical record, verify in Public Cloud:
   - [ ] Record exists
   - [ ] Vendor correct
   - [ ] Material correct
   - [ ] Price correct
   - [ ] Purchasing org correct
   - [ ] Plant correct
   - [ ] Delivery time correct

**Pass Criteria:**
- 100% of critical info records verified correct

**Fail Actions:**
- Any error in critical records is a critical issue
- Correct immediately
- May require manual adjustment in Public Cloud

---

## Validation 3.6: Pricing Completeness

**Purpose:** Ensure all prices imported (no zero or missing prices).

**Query (Public Cloud):**
```sql
SELECT 
    'Zero Price' as "Issue",
    COUNT(*) as "Count"
FROM 
    I_PurchasingInfoRecord
WHERE 
    NetPriceAmount = 0
    OR NetPriceAmount IS NULL

UNION ALL

SELECT 
    'Missing Currency' as "Issue",
    COUNT(*)
FROM 
    I_PurchasingInfoRecord
WHERE 
    Currency IS NULL
    OR Currency = '';
```

**Pass Criteria:**
- Zero prices only for known consignment/free items
- No missing currencies

**Fail Actions:**
- Document all zero prices
- Get business approval or correct
- Fix missing currencies

---

## Validation 3.7: Purchasing Organization Assignment

**Purpose:** Verify info records are assigned to correct purchasing organizations.

**Query (Public Cloud):**
```sql
SELECT 
    PurchasingOrganization,
    COUNT(*) as "Info Record Count"
FROM 
    I_PurchasingInfoRecord
WHERE 
    IsDeleted = ''
GROUP BY 
    PurchasingOrganization
ORDER BY 
    PurchasingOrganization;
```

**Pass Criteria:**
- Distribution matches expected (compare to extraction summary)

**Fail Actions:**
- Investigate unexpected purchasing org assignments
- Correct if errors found

---

## Validation 3.8: Delivery Time Validation

**Purpose:** Ensure delivery times are reasonable and match source.

**Query (Public Cloud):**
```sql
SELECT 
    'Delivery Time = 0' as "Check",
    COUNT(*) as "Count"
FROM 
    I_PurchasingInfoRecord
WHERE 
    PlannedDeliveryTime = 0

UNION ALL

SELECT 
    'Delivery Time > 365 days' as "Check",
    COUNT(*)
FROM 
    I_PurchasingInfoRecord
WHERE 
    PlannedDeliveryTime > 365;
```

**Pass Criteria:**
- Zero delivery times are acceptable if documented
- Long delivery times (> 365) should be reviewed

**Fail Actions:**
- Review and get business approval for extreme values
- Correct if errors

---

## Stage 3 Validation Checklist

After import, confirm:

- [ ] Import success rate ≥ 95%
- [ ] Record count matches template
- [ ] Price spot check 100% accurate
- [ ] Vendor-material counts match
- [ ] All critical info records verified
- [ ] No unexpected zero prices
- [ ] Purchasing org distribution correct
- [ ] Delivery times reasonable

**Overall Pass Criteria:** All checklist items checked

---

# Stage 4: Reconciliation (Source vs Target)

Final comprehensive reconciliation between ECC and Public Cloud.

## Reconciliation 4.1: Full Record Count Comparison

**Purpose:** Compare total counts between systems.

| Metric | ECC Source | Public Cloud | Variance | % |
|--------|------------|--------------|----------|---|
| Total Info Records | _______ | _______ | _______ | ___% |
| Unique Vendors | _______ | _______ | _______ | ___% |
| Unique Materials | _______ | _______ | _______ | ___% |
| Records with Price > 0 | _______ | _______ | _______ | ___% |

**Pass Criteria:**
- All variances < 1% OR explained

**Fail Actions:**
- Investigate variances > 1%
- Document reasons for variances
- Re-import if significant data loss

---

## Reconciliation 4.2: Sample Record Comparison

**Purpose:** Detail comparison of sample records.

**Method:**
1. Select 50 random info records
2. For each record, compare all fields between ECC and Public Cloud
3. Document discrepancies

**Fields to Compare:**
- Vendor
- Material
- Purchasing Organization
- Plant
- Net Price
- Price Unit
- Currency
- Planned Delivery Time
- Min Order Quantity
- Max Order Quantity
- Incoterms
- Tax Code

**Pass Criteria:**
- 98% field accuracy across sample

**Fail Actions:**
- If < 98%, expand sample
- Identify systematic transformation errors
- Correct and re-import if necessary

---

## Reconciliation 4.3: Price Comparison Report

**Purpose:** Ensure price integrity in migration.

**Method:**
1. Export prices from ECC (Vendor, Material, Org, Plant, Price, Currency)
2. Export prices from Public Cloud (same fields)
3. Match records and compare prices
4. Identify discrepancies

**Acceptance Criteria:**
- Price differences ≤ 0.01 (due to rounding)
- Currency must match exactly
- Price unit must match exactly

**Fail Actions:**
- Investigate all price discrepancies
- Correct significant errors (> 1% difference)

---

## Reconciliation 4.4: Missing Records Analysis

**Purpose:** Identify records in ECC but not in Public Cloud.

**Method:**
1. Create list of all info records from ECC: Vendor + Material + Org + Plant
2. Create list of all info records from Public Cloud: Vendor + Material + Org + Plant
3. Identify records in ECC list but not in Public Cloud list

**Pass Criteria:**
- No missing records, OR
- All missing records are documented exclusions

**Fail Actions:**
- Investigate missing records
- Determine if they should have been migrated
- Re-import missing records if necessary

---

## Reconciliation 4.5: Extra Records Analysis

**Purpose:** Identify records in Public Cloud but not in ECC.

**Method:**
Same as 4.4, but identify records in Public Cloud that are not in ECC.

**Pass Criteria:**
- No extra records (should be 0)

**Fail Actions:**
- Investigate source of extra records
- May indicate duplicate imports or incorrect data

---

## Final Reconciliation Report

**Summary Table:**

| Validation Area | Pass/Fail | Notes |
|----------------|-----------|-------|
| Record Count Match | [ ] | Variance: ___% |
| Vendor Count Match | [ ] | Variance: ___% |
| Material Count Match | [ ] | Variance: ___% |
| Sample Field Accuracy | [ ] | Accuracy: ___% |
| Price Integrity | [ ] | Discrepancies: ___ |
| Missing Records | [ ] | Count: ___ |
| Extra Records | [ ] | Count: ___ |

**Overall Reconciliation Pass Criteria:**
- All areas marked "Pass"
- All variances explained and approved

---

## Error Scenario Reference

### Common Errors and Resolutions

#### Error 1: "Vendor does not exist"
- **Cause:** Vendor not migrated to Public Cloud
- **Resolution:** Migrate vendor first, then re-import info record

#### Error 2: "Material does not exist"
- **Cause:** Material not migrated to Public Cloud
- **Resolution:** Migrate material first, then re-import info record

#### Error 3: "Invalid purchasing organization"
- **Cause:** Purchasing org code doesn't match Public Cloud
- **Resolution:** Create org structure in Public Cloud or map to correct code

#### Error 4: "Invalid unit of measure"
- **Cause:** UoM from ECC doesn't exist in Public Cloud
- **Resolution:** Create UoM in Public Cloud or map to existing UoM

#### Error 5: "Duplicate record"
- **Cause:** Info record already exists in Public Cloud
- **Resolution:** Use update mode instead of create, or check if truly duplicate

#### Error 6: "Invalid currency"
- **Cause:** Currency code not recognized
- **Resolution:** Use valid ISO 4217 code, create currency in Public Cloud if needed

#### Error 7: "Price must be positive"
- **Cause:** Price = 0 or negative
- **Resolution:** Either provide valid price or document as consignment/free item

#### Error 8: "Invalid price unit"
- **Cause:** Price unit not in allowed values
- **Resolution:** Use 1, 10, 100, or 1000 (most systems)

---

## Validation Tools and Scripts

### Excel Macro for Bulk Validation

```vba
Sub ValidateSupplierInfoTemplate()
    Dim ws As Worksheet
    Dim lastRow As Long
    Dim errorCount As Integer
    
    Set ws = ActiveSheet
    lastRow = ws.Cells(ws.Rows.Count, "A").End(xlUp).Row
    errorCount = 0
    
    ' Add validation column header
    ws.Cells(1, 30).Value = "Validation Status"
    
    ' Loop through each row
    For i = 2 To lastRow
        Dim status As String
        status = "OK"
        
        ' Check required fields
        If IsEmpty(ws.Cells(i, 1)) Then status = "Missing Vendor"
        If IsEmpty(ws.Cells(i, 2)) Then status = "Missing Material"
        If IsEmpty(ws.Cells(i, 10)) Then status = "Missing Price"
        
        ' Check numeric fields
        If Not IsNumeric(ws.Cells(i, 10)) And Not IsEmpty(ws.Cells(i, 10)) Then
            status = "Invalid Price"
        End If
        
        ' Write status
        ws.Cells(i, 30).Value = status
        
        If status <> "OK" Then errorCount = errorCount + 1
    Next i
    
    MsgBox "Validation complete. Errors found: " & errorCount
End Sub
```

---

## Validation Schedule

Recommended validation schedule:

| Stage | When | Duration | Responsible |
|-------|------|----------|-------------|
| Pre-Extraction Validation | Before extraction | 2 hours | SAP ECC Team |
| Template Validation | After transformation | 2 hours | Migration Team |
| Post-Import Validation | Immediately after import | 3 hours | Migration Team |
| Reconciliation | After all imports complete | 4 hours | Migration Team + Business |
| Final Sign-Off | After UAT | 2 hours | Business Owners |

---

## Document Version

- **Created:** [Date]
- **Last Updated:** [Date]
- **Project:** SAP ECC 6.0 to SAP ERP Public Cloud Migration
- **Author:** Migration Team


