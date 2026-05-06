# Wave 2: Business Partner & Material Master - Execution Runbook

**Document Version:** 1.0  
**Wave Name:** Wave 2 - Business Partner & Material Master  
**Timing:** T-3 weeks before Go-Live  
**Duration:** 5-7 days  
**Objects Covered:** 10 data objects (BP Vendors, BP Customers, Material Master, Info Records, Source Lists, Quota Arrangements, BOMs, Pricing Conditions, Credit Accounts, Customer Material Info)

---

## Document Purpose

This runbook provides step-by-step technical procedures for executing Wave 2 data migration. It is designed for the migration team to follow during the actual migration window. Use this document together with the Wave 2 Dependencies Flow Diagram for execution guidance.

---

## Table of Contents

1. [Prerequisites & Readiness](#prerequisites--readiness)
2. [Pre-Migration Activities](#pre-migration-activities)
3. [Data Object Execution Procedures](#data-object-execution-procedures)
   - [2.1 Business Partners](#21-business-partners)
     - [BP - Vendors (Supplier)](#bp---vendors-supplier)
     - [BP - Customers](#bp---customers)
   - [2.2 Material Master](#22-material-master)
     - [Material Master](#material-master)
   - [2.3 Procurement Master Data](#23-procurement-master-data)
     - [Purchasing Info Records](#purchasing-info-records)
     - [Source Lists](#source-lists)
     - [Quota Arrangements](#quota-arrangements)
   - [2.4 Production Master Data](#24-production-master-data)
     - [Bill of Materials (BOM)](#bill-of-materials-bom)
   - [2.5 Sales Master Data](#25-sales-master-data)
     - [Customer Pricing Conditions](#customer-pricing-conditions)
     - [Credit Accounts](#credit-accounts)
     - [Customer Material Info](#customer-material-info)
4. [Wave 2 Load Sequence](#wave-2-load-sequence)
5. [Validation & Sign-Off Checklist](#validation--sign-off-checklist)
6. [Troubleshooting Reference](#troubleshooting-reference)

---

## Prerequisites & Readiness

### Wave 1 Completion Requirements

Before starting Wave 2, verify that Wave 1 is complete and validated:

- [ ] All Wave 1 objects successfully migrated (14 objects)
- [ ] Wave 1 validation checklist signed off
- [ ] GL Accounts are active and ready for posting
- [ ] Cost Centers and Profit Centers are configured
- [ ] Bank Master Data loaded
- [ ] Payment Terms configured
- [ ] Tax Codes configured
- [ ] Asset Master loaded (if applicable)
- [ ] No critical errors remaining in Wave 1 migration logs

### System Readiness

- [ ] S/4HANA system available and accessible
- [ ] Migration Cockpit configured and tested
- [ ] All migration templates imported and validated
- [ ] Network connectivity to ECC source system verified
- [ ] Sufficient storage space for data files (minimum 10 GB free)
- [ ] All technical user IDs active with proper authorizations

### Team Readiness

- [ ] Migration team members available for full wave duration
- [ ] Functional leads (FI, MM, SD, PP) on standby for validation
- [ ] Communication channels established (Teams, Email, etc.)
- [ ] Escalation contacts confirmed and available
- [ ] Backup team members identified

---

## Pre-Migration Activities

### Activity 1: Template Downloads & Setup

Download all required migration templates from Migration Cockpit:

- [ ] Download BP_VENDOR template (Business Partner - Vendor)
- [ ] Download BP_CUSTOMER template (Business Partner - Customer)
- [ ] Download MM_MATERIAL_MASTER template (Material Master)
- [ ] Download MM_INFO_RECORD template (Purchasing Info Records)
- [ ] Download MM_SOURCE_LIST template (Source Lists)
- [ ] Download SD_PRICING template (Customer Pricing Conditions)
- [ ] Download SD_CUST_MATERIAL template (Customer Material Info)
- [ ] Verify template versions match S/4HANA release
- [ ] Review all mandatory fields in each template

**Transaction Codes:**
- `LTMC` - Migration Cockpit (main transaction)
- `LTMOM` - Migration Object Modeler

### Activity 2: Source Data Extraction from ECC

Extract data from ECC system using the following methods:

**Vendor Master Extraction:**
- [ ] Run report to extract active vendors from ECC
- [ ] Include all company codes: SG21, CN13, CN17, US10, BE10, HCIL, BR10
- [ ] Extract vendor general data, company code data, purchasing data
- [ ] Export to flat file format (CSV or Excel)

**ECC Tables for Vendors:**
- `LFA1` - Vendor Master (General Section)
- `LFB1` - Vendor Company Code Data
- `LFM1` - Vendor Purchasing Organization Data
- `LFBK` - Vendor Bank Details

**Customer Master Extraction:**
- [ ] Run report to extract active customers from ECC
- [ ] Include sales organization and distribution channel data
- [ ] Extract customer general data, company code data, sales area data
- [ ] Export to flat file format

**ECC Tables for Customers:**
- `KNA1` - Customer Master (General Section)
- `KNB1` - Customer Company Code Data
- `KNVV` - Customer Sales Area Data

**Material Master Extraction:**
- [ ] Extract active materials from ECC (if applicable)
- [ ] Extract material master data from Smart-Fulfillment System spreadsheets
- [ ] Include all views: Basic Data, MRP, Procurement, Sales, Accounting
- [ ] Export to flat file format

**ECC Tables for Materials:**
- `MARA` - Material General Data
- `MARC` - Material Plant Data
- `MARD` - Material Storage Location Data
- `MBEW` - Material Valuation Data

**Other Master Data Extraction:**
- [ ] Extract existing Info Records from ECC (if any)
- [ ] Extract existing BOMs from ECC or manual sources
- [ ] Extract pricing conditions from ECC
- [ ] Extract customer material info records from ECC

### Activity 3: Data Quality Assessment

Before starting migration, assess data quality:

- [ ] Run duplicate check on vendor numbers
- [ ] Run duplicate check on customer numbers
- [ ] Run duplicate check on material numbers
- [ ] Verify all mandatory fields are populated
- [ ] Check for invalid characters in name fields
- [ ] Verify bank details are complete (IBAN, SWIFT)
- [ ] Check for missing reconciliation accounts
- [ ] Validate tax registration numbers format
- [ ] Generate data quality report

### Activity 4: Workspace Preparation

Set up the migration workspace:

- [ ] Create working directory structure for Wave 2 files
- [ ] Set up naming convention: `WAVE2_OBJECT_DATE_VERSION.xlsx`
- [ ] Prepare backup location for source files
- [ ] Create error log folder
- [ ] Set up validation reports folder
- [ ] Prepare reconciliation spreadsheet templates

---

## Data Object Execution Procedures

## 2.1 Business Partners

### BP - Vendors (Supplier)

**Object Details:**
- **Object ID:** 15
- **Source:** ECC
- **Dependencies:** GL Accounts, Payment Terms, Bank Master
- **Complexity:** High
- **Volume:** <1,200 vendors
- **Migration Tool:** BP_VENDOR template (Migration Cockpit)
- **Priority:** Critical
- **Estimated Duration:** 6-8 hours

#### Data Preparation & Cleansing

**Step 1: Extract Vendor Data from ECC**

- [ ] Execute extraction from ECC tables (LFA1, LFB1, LFM1, LFBK)
- [ ] Filter for active vendors only (deletion flag not set)
- [ ] Include all company codes
- [ ] Include all purchasing organizations

**Step 2: Data Quality Checks**

- [ ] Check for duplicate vendor numbers
- [ ] Verify vendor names are complete (no truncated names)
- [ ] Validate street addresses are complete
- [ ] Check postal codes match country format
- [ ] Verify tax ID numbers are present for tax-relevant vendors
- [ ] Validate bank account numbers (IBAN format for international)
- [ ] Check payment terms exist in S/4HANA (from Wave 1)
- [ ] Verify reconciliation accounts are valid GL accounts

**Step 3: Data Cleansing Rules**

Apply these cleansing rules to vendor data:

- [ ] Remove special characters from vendor names: `@`, `#`, `$`, `%`, `^`, `&`, `*`
- [ ] Standardize country codes to ISO 2-digit format (e.g., US, CN, SG)
- [ ] Convert phone numbers to international format: `+[country code] [number]`
- [ ] Validate email addresses have proper format: `name@domain.com`
- [ ] Set language key based on country (EN for US, ZH for CN, etc.)
- [ ] Remove inactive purchasing info records references
- [ ] Update vendor account groups to match S/4HANA configuration

**Step 4: Field Mapping**

Map ECC fields to S/4HANA Business Partner structure:

| ECC Field | ECC Table | S/4HANA BP Field | Transformation Rule |
|-----------|-----------|------------------|---------------------|
| LIFNR | LFA1 | Business Partner Number | Map to number range Z001 (BOM/NPR), Z002 (IC), ZEMP (Employee), ZCPD (One-time) |
| NAME1 | LFA1 | Name | Copy as-is, remove special chars |
| STRAS | LFA1 | Street | Copy as-is |
| ORT01 | LFA1 | City | Copy as-is |
| PSTLZ | LFA1 | Postal Code | Copy as-is |
| LAND1 | LFA1 | Country | Convert to ISO 2-digit |
| STCEG | LFA1 | VAT Registration Number | Copy as-is |
| AKONT | LFB1 | Reconciliation Account | Validate exists in S/4HANA |
| ZTERM | LFB1 | Payment Terms | Validate exists in S/4HANA |
| BANKS | LFBK | Bank Country | Convert to ISO format |
| BANKL | LFBK | Bank Key | Validate against Bank Master |
| BANKN | LFBK | Bank Account Number | Copy as-is |
| IBAN | LFBK | IBAN | Validate IBAN format |
| EKORG | LFM1 | Purchasing Organization | Map to S/4HANA org |

**Step 5: Special Handling**

- [ ] **Number Range Assignment:** Assign vendors to correct number ranges
  - Z001 (0000100000-0009999999): BOM/NPR Vendors (internal assignment)
  - Z002 (AAAA-ZZZZ): Inter-company Vendors (external)
  - ZCPD (0000000001-0000000999): One-time Vendors (external)
  - ZEMP (0000010000-0000099999): Employee Vendors (internal)
- [ ] **Inter-company Vendors:** Flag and verify all IC vendor relationships
- [ ] **Employee Vendors:** Separate employee reimbursement vendors
- [ ] **Inactive Vendors:** Exclude vendors with no activity in last 2 years

#### Load Execution

**Step 1: Prepare Migration File**

- [ ] Open BP_VENDOR template downloaded from Migration Cockpit
- [ ] Copy cleansed vendor data into template
- [ ] Ensure all mandatory fields are populated:
  - Business Partner Number
  - Name
  - Country
  - Company Code
  - Reconciliation Account
  - Payment Terms
- [ ] Save file as: `WAVE2_BP_VENDOR_[DATE]_V1.xlsx`
- [ ] Create backup copy of file

**Step 2: Load into Migration Cockpit**

- [ ] Log into S/4HANA system
- [ ] Execute transaction `LTMC` (Migration Cockpit)
- [ ] Select migration project: "HOME_CONTROL_MIGRATION_WAVE2"
- [ ] Select migration object: "Business Partner - Vendor"
- [ ] Click "Create" to create new migration run
- [ ] Enter run name: `VENDOR_LOAD_[DATE]`
- [ ] Upload prepared Excel file
- [ ] Review field mappings - confirm all fields mapped correctly

**Step 3: File Format & Key Parameters**

- [ ] File format: Excel (.xlsx) or CSV (UTF-8 encoding)
- [ ] Separator: Tab or comma (for CSV)
- [ ] Date format: `YYYY-MM-DD`
- [ ] Number format: No thousand separators, decimal = period
- [ ] Text qualifier: Double quotes for CSV

**Key Configuration Parameters in Migration Cockpit:**
- [ ] **Simulation Mode:** Set to "Yes" for first run
- [ ] **Commit Block Size:** 50 records (for large volumes)
- [ ] **Error Handling:** Stop on critical errors
- [ ] **Duplicate Check:** Enabled
- [ ] **Update Mode:** Create new records only (not update existing)

**Step 4: Execute Load**

- [ ] Click "Start Data Import" button
- [ ] Monitor import progress in real-time
- [ ] Review any warning or error messages immediately
- [ ] Download migration log after completion
- [ ] Check statistics: Total records, Successful, Errors, Warnings

**Step 5: Error Resolution (if needed)**

If errors occur during load:
- [ ] Download error log from Migration Cockpit
- [ ] Review each error message and root cause
- [ ] Categorize errors: Master data errors, Field mapping errors, System errors
- [ ] Correct errors in source file
- [ ] Create new migration run with corrected data
- [ ] Re-execute load for error records only

#### Pre-Import Validation

Perform these checks BEFORE loading into S/4HANA:

- [ ] **Record Count Check:** Count of vendors in source file matches ECC extraction
- [ ] **Mandatory Field Check:** All mandatory fields populated (no blanks)
- [ ] **Reconciliation Account Check:** All recon accounts exist in S/4HANA GL master
- [ ] **Payment Terms Check:** All payment terms exist in S/4HANA
- [ ] **Bank Account Check:** All bank keys exist in Bank Master
- [ ] **Number Range Check:** All vendor numbers fall within assigned number ranges
- [ ] **Duplicate Check:** No duplicate vendor numbers in file
- [ ] **Company Code Check:** All company codes are valid and active
- [ ] **Data Format Check:** All dates, numbers, and text fields follow correct format
- [ ] **Cross-Reference Check:** Any cross-references to other vendors are valid

#### Post-Import Validation

Perform these checks AFTER loading into S/4HANA:

**Step 1: Record Count Validation**

- [ ] Count total vendors loaded in S/4HANA
- [ ] Compare to source ECC count
- [ ] Variance must be zero (100% match)
- [ ] Document any missing vendors with justification

**Transaction Code:** `BP` (Business Partner transaction)

**Step 2: Master Data Completeness Check**

- [ ] Open sample vendors in BP transaction
- [ ] Verify all fields populated correctly:
  - General data (name, address, contact)
  - Company code data (reconciliation account, payment terms)
  - Purchasing data (purchasing org, payment terms)
  - Bank details (bank key, account number, IBAN)
- [ ] Check 10% sample across all number ranges

**Step 3: System Access Validation**

- [ ] Create test purchase requisition with sample vendor
- [ ] Verify vendor is selectable in purchasing documents
- [ ] Test vendor search functionality (by name, by number)
- [ ] Verify vendor bank details are accessible
- [ ] Test payment run with sample vendor (simulation mode)

**Transaction Codes:**
- `ME51N` - Create Purchase Requisition
- `F110` - Payment Run

**Step 4: Functional Testing**

- [ ] **Purchasing Test:**
  - Create purchase order for sample vendor
  - Verify payment terms are correctly defaulted
  - Verify purchasing organization data is correct
- [ ] **AP Invoice Test:**
  - Create sample invoice for vendor (if allowed in non-prod)
  - Verify reconciliation account is posted correctly
  - Verify tax code defaults correctly
- [ ] **Payment Test:**
  - Run payment proposal for sample vendor invoices
  - Verify bank details are picked up correctly
  - Verify payment method is correct

**Transaction Codes:**
- `ME21N` - Create Purchase Order
- `MIRO` - Enter Invoice Receipt
- `F110` - Payment Run

**Step 5: Integration Validation**

- [ ] Verify vendor master sync with any external systems
- [ ] Test vendor data availability in reporting
- [ ] Check vendor data in Fiori apps
- [ ] Validate vendor search in S/4HANA Fiori launchpad

**Step 6: Reconciliation Report**

Generate and review these reports:

- [ ] Vendor Master List (S/4HANA)
- [ ] Compare to ECC Vendor Master List
- [ ] Reconcile differences
- [ ] Document any exclusions or transformations

**Transaction Code:** `S_ALR_87012089` (Vendor Master List)

---

### BP - Customers

**Object Details:**
- **Object ID:** 16
- **Source:** ECC
- **Dependencies:** GL Accounts, Payment Terms
- **Complexity:** Medium
- **Volume:** TBD (to be determined based on extraction)
- **Migration Tool:** BP_CUSTOMER template (Migration Cockpit)
- **Priority:** Critical
- **Estimated Duration:** 4-6 hours

#### Data Preparation & Cleansing

**Step 1: Extract Customer Data from ECC**

- [ ] Execute extraction from ECC tables (KNA1, KNB1, KNVV)
- [ ] Filter for active customers only (deletion flag not set)
- [ ] Include all company codes
- [ ] Include all sales organizations and distribution channels

**Step 2: Data Quality Checks**

- [ ] Check for duplicate customer numbers
- [ ] Verify customer names are complete
- [ ] Validate street addresses are complete
- [ ] Check postal codes match country format
- [ ] Verify tax ID numbers are present
- [ ] Check payment terms exist in S/4HANA
- [ ] Verify reconciliation accounts are valid GL accounts
- [ ] Validate credit control area assignments
- [ ] Check pricing procedures are configured

**Step 3: Data Cleansing Rules**

Apply these cleansing rules to customer data:

- [ ] Remove special characters from customer names
- [ ] Standardize country codes to ISO 2-digit format
- [ ] Convert phone numbers to international format
- [ ] Validate email addresses format
- [ ] Set language key based on country
- [ ] Update customer account groups to match S/4HANA configuration
- [ ] Clean up duplicate customer addresses

**Step 4: Field Mapping**

Map ECC fields to S/4HANA Business Partner structure:

| ECC Field | ECC Table | S/4HANA BP Field | Transformation Rule |
|-----------|-----------|------------------|---------------------|
| KUNNR | KNA1 | Business Partner Number | Copy as-is or map to new number range |
| NAME1 | KNA1 | Name | Copy as-is, remove special chars |
| STRAS | KNA1 | Street | Copy as-is |
| ORT01 | KNA1 | City | Copy as-is |
| PSTLZ | KNA1 | Postal Code | Copy as-is |
| LAND1 | KNA1 | Country | Convert to ISO 2-digit |
| STCEG | KNA1 | VAT Registration Number | Copy as-is |
| AKONT | KNB1 | Reconciliation Account | Validate exists in S/4HANA |
| ZTERM | KNB1 | Payment Terms | Validate exists in S/4HANA |
| KTOKD | KNA1 | Account Group | Map to S/4HANA customer group |
| VKORG | KNVV | Sales Organization | Map to S/4HANA org |
| VTWEG | KNVV | Distribution Channel | Map to S/4HANA |
| SPART | KNVV | Division | Map to S/4HANA |
| KDGRP | KNVV | Customer Group | Map to S/4HANA |

**Step 5: Special Handling**

- [ ] **Credit Management:** Verify credit control area assignments
- [ ] **Pricing:** Ensure customer pricing procedure is configured
- [ ] **Sales Area Data:** Load all relevant sales org/dist channel combinations
- [ ] **Partner Functions:** Define required partner functions (sold-to, ship-to, bill-to, payer)

#### Load Execution

**Step 1: Prepare Migration File**

- [ ] Open BP_CUSTOMER template from Migration Cockpit
- [ ] Copy cleansed customer data into template
- [ ] Ensure all mandatory fields populated:
  - Business Partner Number
  - Name
  - Country
  - Company Code
  - Reconciliation Account
  - Sales Organization
  - Distribution Channel
  - Division
- [ ] Save file as: `WAVE2_BP_CUSTOMER_[DATE]_V1.xlsx`
- [ ] Create backup copy

**Step 2: Load into Migration Cockpit**

- [ ] Execute transaction `LTMC`
- [ ] Select migration project: "HOME_CONTROL_MIGRATION_WAVE2"
- [ ] Select migration object: "Business Partner - Customer"
- [ ] Create new migration run: `CUSTOMER_LOAD_[DATE]`
- [ ] Upload prepared Excel file
- [ ] Review field mappings

**Step 3: File Format & Key Parameters**

- [ ] File format: Excel (.xlsx) or CSV (UTF-8)
- [ ] Date format: `YYYY-MM-DD`
- [ ] Number format: No thousand separators

**Configuration Parameters:**
- [ ] Simulation Mode: Yes (first run)
- [ ] Commit Block Size: 50 records
- [ ] Error Handling: Stop on critical errors
- [ ] Duplicate Check: Enabled

**Step 4: Execute Load**

- [ ] Click "Start Data Import"
- [ ] Monitor progress
- [ ] Review messages
- [ ] Download migration log
- [ ] Check statistics

**Step 5: Error Resolution**

- [ ] Review error log
- [ ] Correct errors in source file
- [ ] Re-load error records

#### Pre-Import Validation

- [ ] Record count matches ECC extraction
- [ ] All mandatory fields populated
- [ ] Reconciliation accounts exist in GL master
- [ ] Payment terms exist in S/4HANA
- [ ] Sales organizations are valid
- [ ] No duplicate customer numbers
- [ ] Company codes are valid
- [ ] Credit control areas are configured
- [ ] Pricing procedures are set up
- [ ] Data format checks pass

#### Post-Import Validation

**Step 1: Record Count Validation**

- [ ] Count total customers in S/4HANA
- [ ] Compare to source ECC count
- [ ] Document any variances

**Transaction Code:** `BP` or `XD03` (Display Customer)

**Step 2: Master Data Completeness**

- [ ] Open sample customers in BP transaction
- [ ] Verify all fields populated:
  - General data
  - Company code data
  - Sales area data
  - Credit management data
- [ ] Check 10% sample

**Step 3: System Access Validation**

- [ ] Create test sales order with sample customer
- [ ] Verify customer is selectable
- [ ] Test customer search functionality
- [ ] Verify credit check is working

**Transaction Codes:**
- `VA01` - Create Sales Order
- `VKM1` - Create Customer Credit Master

**Step 4: Functional Testing**

- [ ] **Sales Order Test:**
  - Create sales order for sample customer
  - Verify pricing is working
  - Verify payment terms default correctly
  - Check tax determination
- [ ] **AR Invoice Test:**
  - Create sample invoice (if allowed)
  - Verify reconciliation account posting
  - Verify tax code defaults
- [ ] **Credit Management Test:**
  - Check customer credit limit
  - Test credit check in sales order

**Transaction Codes:**
- `VA01` - Create Sales Order
- `VF01` - Create Billing Document
- `FD32` - Change Customer Credit Management

**Step 5: Integration Validation**

- [ ] Verify customer sync with external systems
- [ ] Check customer data in Fiori apps
- [ ] Validate customer search in S/4HANA

**Step 6: Reconciliation Report**

- [ ] Generate Customer Master List in S/4HANA
- [ ] Compare to ECC Customer Master List
- [ ] Reconcile differences
- [ ] Document exclusions

**Transaction Code:** `S_ALR_87012179` (Customer Master List)

---

## 2.2 Material Master

### Material Master

**Object Details:**
- **Object ID:** 17
- **Source:** Spreadsheet/ECC
- **Dependencies:** GL Accounts, Material Groups
- **Complexity:** Medium
- **Volume:** Hundreds
- **Migration Tool:** MM_MATERIAL_MASTER template / API
- **Priority:** Critical
- **Estimated Duration:** 8-12 hours

#### Data Preparation & Cleansing

**Step 1: Extract Material Data**

- [ ] Gather material master data from Smart-Fulfillment System spreadsheets
- [ ] Extract any existing materials from ECC (if applicable)
- [ ] Consolidate material data from all sources
- [ ] Include all material types: ZFER (Finished Goods), ZH01-ZH44 (Components), ZHL1-ZHL2 (Semi-finished)

**Step 2: Data Quality Checks**

- [ ] Check for duplicate material numbers
- [ ] Verify material descriptions are complete
- [ ] Validate base unit of measure (UOM) is correct
- [ ] Check material type assignments
- [ ] Verify material group assignments
- [ ] Validate valuation class assignments
- [ ] Check profit center assignments (if required)
- [ ] Verify MRP type and lot size data
- [ ] Validate purchasing data (purchase order text, purchasing group)
- [ ] Check sales data (sales org, item category group)

**Step 3: Data Cleansing Rules**

Apply these cleansing rules:

- [ ] Standardize material descriptions (consistent naming convention)
- [ ] Validate UOM codes against S/4HANA standard codes
- [ ] Remove special characters from descriptions
- [ ] Standardize material numbers format
- [ ] Validate material type codes match S/4HANA configuration
- [ ] Check material groups are configured in S/4HANA
- [ ] Verify valuation classes exist in system

**Step 4: Field Mapping**

Map source fields to S/4HANA Material Master structure:

| Source Field | S/4HANA Field | View | Transformation Rule |
|--------------|---------------|------|---------------------|
| Material Number | MATNR | Basic Data | Copy as-is or generate new |
| Material Description | MAKTX | Basic Data | Copy, remove special chars |
| Material Type | MTART | Basic Data | Map to configured types |
| Base UOM | MEINS | Basic Data | Validate against UOM master |
| Material Group | MATKL | Basic Data | Map to S/4HANA material groups |
| Gross Weight | BRGEW | Basic Data | Copy as-is |
| Net Weight | NTGEW | Basic Data | Copy as-is |
| Weight Unit | GEWEI | Basic Data | Validate against UOM master |
| Valuation Class | BKLAS | Accounting | Map to S/4HANA valuation classes |
| Price Control | VPRSV | Accounting | S (Standard) or V (Moving Avg) |
| Standard Price | STPRS | Accounting | Copy as-is |
| Moving Price | VERPR | Accounting | Copy as-is |
| MRP Type | DISMM | MRP | Map MRP type codes |
| Lot Size | DISLS | MRP | EX, FX, or other |
| Procurement Type | BESKZ | MRP | E (In-house), F (External) |
| Purchasing Group | EKGRP | Purchasing | Map to S/4HANA purch groups |
| Profit Center | PRCTR | Accounting | Validate against profit center master |

**Step 5: Special Handling**

- [ ] **Special UOM:** Ensure UOM "ZPC" is configured with 3 decimal places
- [ ] **Integration:** Coordinate with Smart-Fulfillment System for material number assignment
- [ ] **BOMs:** Mark materials that will have BOMs (for next step)
- [ ] **Batch Management:** Set batch management indicator if required
- [ ] **Serial Numbers:** Configure serial number profile if needed
- [ ] **Material Status:** Set plant-specific material status if applicable

#### Load Execution

**Step 1: Prepare Migration File**

- [ ] Open MM_MATERIAL_MASTER template
- [ ] Copy cleansed material data into template
- [ ] Ensure all mandatory fields populated:
  - Material Number
  - Material Description
  - Material Type
  - Base UOM
  - Material Group
  - Valuation Class
  - Plant
- [ ] Include all required views: Basic, MRP, Purchasing, Sales, Accounting
- [ ] Save file as: `WAVE2_MATERIAL_MASTER_[DATE]_V1.xlsx`
- [ ] Create backup copy

**Step 2: Load into Migration Cockpit**

- [ ] Execute transaction `LTMC`
- [ ] Select migration project: "HOME_CONTROL_MIGRATION_WAVE2"
- [ ] Select migration object: "Material Master"
- [ ] Create new migration run: `MATERIAL_LOAD_[DATE]`
- [ ] Upload prepared Excel file
- [ ] Review field mappings for all views

**Alternative: API Load**

If using API for integration with Smart-Fulfillment System:
- [ ] Configure API endpoint in S/4HANA
- [ ] Test API connection
- [ ] Map JSON/XML structure to material master fields
- [ ] Execute API call with sample records
- [ ] Validate API response
- [ ] Execute bulk API load

**Step 3: File Format & Key Parameters**

- [ ] File format: Excel (.xlsx) or CSV (UTF-8)
- [ ] Multiple sheets may be needed for different views
- [ ] Date format: `YYYY-MM-DD`
- [ ] Decimal format: Period for decimal separator

**Configuration Parameters:**
- [ ] Simulation Mode: Yes (first run)
- [ ] Commit Block Size: 25 records (materials are complex)
- [ ] Error Handling: Continue processing (log errors)
- [ ] Material View Extension: All required views

**Step 4: Execute Load**

- [ ] Click "Start Data Import"
- [ ] Monitor progress carefully (materials take longer)
- [ ] Review any warning or error messages
- [ ] Download migration log
- [ ] Check statistics by material type

**Step 5: Error Resolution**

Common material errors:
- [ ] Material type not found - verify configuration
- [ ] Valuation class not assigned to material type
- [ ] UOM not found - create UOM first
- [ ] Material group not found - create material group
- [ ] Profit center invalid - verify profit center master
- [ ] MRP type invalid - check MRP configuration

#### Pre-Import Validation

- [ ] Record count matches source data
- [ ] All material types are configured in S/4HANA
- [ ] All material groups exist
- [ ] All valuation classes configured
- [ ] All UOMs exist in system (especially ZPC)
- [ ] No duplicate material numbers
- [ ] All plants are valid
- [ ] Profit centers are valid (if used)
- [ ] MRP types are configured
- [ ] Purchasing groups exist
- [ ] Data format checks pass

#### Post-Import Validation

**Step 1: Record Count Validation**

- [ ] Count total materials in S/4HANA by material type
- [ ] Compare to source counts
- [ ] Variance must be zero

**Transaction Code:** `MM60` (Material List)

**Step 2: Master Data Completeness**

- [ ] Open sample materials in material master transaction
- [ ] Verify all views populated correctly:
  - Basic Data view
  - MRP view
  - Purchasing view
  - Sales view (if applicable)
  - Accounting view
  - Quality Management view (if needed)
- [ ] Check 15% sample across all material types

**Transaction Code:** `MM03` (Display Material)

**Step 3: System Access Validation**

- [ ] Create test purchase requisition with sample material
- [ ] Verify material is selectable
- [ ] Test material search functionality
- [ ] Verify MRP run can process materials
- [ ] Test BOM creation for finished goods (next step)

**Transaction Codes:**
- `ME51N` - Create Purchase Requisition
- `MD01` - MRP Run
- `CS01` - Create BOM

**Step 4: Functional Testing**

- [ ] **MRP Test:**
  - Run MRP for sample plant
  - Verify planning proposals are created
  - Check lot sizing calculation
- [ ] **Purchasing Test:**
  - Create purchase order for sample materials
  - Verify purchasing data defaults correctly
  - Check purchasing info record creation
- [ ] **Inventory Test:**
  - Post sample goods receipt (if allowed)
  - Verify accounting document posted correctly
  - Check valuation and quantity update
- [ ] **Sales Test (if sales view loaded):**
  - Create sales order with material
  - Verify availability check
  - Check pricing determination

**Transaction Codes:**
- `MD04` - Stock/Requirements List
- `ME21N` - Create Purchase Order
- `MIGO` - Goods Receipt
- `VA01` - Create Sales Order

**Step 5: Integration Validation**

- [ ] Verify material sync with Smart-Fulfillment System
- [ ] Check material master in Fiori apps
- [ ] Validate material search in S/4HANA
- [ ] Test material availability in relevant processes

**Step 6: Accounting Validation**

- [ ] Verify valuation class assignments
- [ ] Check GL account determination for materials
- [ ] Test posting to verify correct GL accounts hit
- [ ] Validate profit center derivation (if used)

**Transaction Code:** `OMWB` (Account Determination Wizard)

**Step 7: Reconciliation Report**

- [ ] Generate Material Master List in S/4HANA
- [ ] Group by material type
- [ ] Compare to source system
- [ ] Document any exclusions or new materials

**Transaction Code:** `MM60` (Material List)

---

## 2.3 Procurement Master Data

### Purchasing Info Records

**Object Details:**
- **Object ID:** 18
- **Source:** Manual/ECC
- **Dependencies:** Vendors, Materials
- **Complexity:** Medium
- **Volume:** None in legacy (to be created)
- **Migration Tool:** MM_INFO_RECORD template (Migration Cockpit)
- **Priority:** High
- **Estimated Duration:** 4-6 hours

#### Data Preparation & Cleansing

**Step 1: Gather Info Record Data**

- [ ] Extract any existing info records from ECC (if applicable)
- [ ] Gather vendor pricing information from purchasing team
- [ ] Collect lead time data for each vendor-material combination
- [ ] Obtain minimum order quantities (MOQ)
- [ ] Get standard pack quantities
- [ ] Identify preferred vendors for each material

**Step 2: Data Quality Checks**

- [ ] Verify all vendor numbers exist in S/4HANA (loaded in previous step)
- [ ] Verify all material numbers exist in S/4HANA (loaded in previous step)
- [ ] Check pricing data is complete (price, currency, unit)
- [ ] Validate lead times are reasonable
- [ ] Check planned delivery times
- [ ] Verify purchasing organizations are valid
- [ ] Validate price unit and order unit

**Step 3: Data Cleansing Rules**

- [ ] Standardize pricing units (align with material base UOM where possible)
- [ ] Convert all prices to standard currency per company code
- [ ] Validate lead times are in days (integer)
- [ ] Remove expired info records (past validity dates)
- [ ] Update vendor-material relationships

**Step 4: Field Mapping**

| Source Field | S/4HANA Field | Transformation Rule |
|--------------|---------------|---------------------|
| Vendor Number | LIFNR | Must exist in vendor master |
| Material Number | MATNR | Must exist in material master |
| Purchasing Organization | EKORG | Validate against org structure |
| Plant | WERKS | Validate against plant master |
| Info Record Category | ESOKZ | 0=Standard, 1=Subcontracting |
| Net Price | NETPR | Numeric, no thousand separators |
| Currency | WAERS | ISO currency code |
| Price Unit | PEINH | Numeric |
| Order Unit | BSTME | Validate against UOM master |
| Planned Delivery Time | APLFZ | Days (integer) |
| Minimum Order Qty | MINBM | Numeric |
| Standard Pack Qty | BSTRF | Numeric |
| Valid From Date | VALID_FROM | YYYY-MM-DD |
| Valid To Date | VALID_TO | YYYY-MM-DD |

**Step 5: Special Handling**

- [ ] **PPCA Workflow:** Use BTP App for PPCA (Product Price Change Approval) workflow
- [ ] **Subcontracting:** Flag info records for subcontractors with special category
- [ ] **Preferred Vendor:** Mark preferred vendor for each material
- [ ] **Price History:** Maintain price change history if available

#### Load Execution

**Step 1: Prepare Migration File**

- [ ] Open MM_INFO_RECORD template
- [ ] Enter info record data
- [ ] Mandatory fields:
  - Vendor Number
  - Material Number
  - Purchasing Organization
  - Plant (optional but recommended)
  - Price
  - Currency
  - Valid From Date
- [ ] Save file as: `WAVE2_INFO_RECORD_[DATE]_V1.xlsx`

**Step 2: Load into Migration Cockpit**

- [ ] Execute transaction `LTMC`
- [ ] Select migration object: "Purchasing Info Record"
- [ ] Create migration run: `INFO_RECORD_LOAD_[DATE]`
- [ ] Upload file
- [ ] Review mappings

**Step 3: Key Parameters**

- [ ] Simulation Mode: Yes
- [ ] Commit Block Size: 100 records
- [ ] Error Handling: Continue processing

**Step 4: Execute Load**

- [ ] Start data import
- [ ] Monitor progress
- [ ] Download log

**Step 5: Error Resolution**

- [ ] Check for vendor not found errors
- [ ] Check for material not found errors
- [ ] Verify purchasing organization errors

#### Pre-Import Validation

- [ ] All vendors exist in S/4HANA
- [ ] All materials exist in S/4HANA
- [ ] Prices are positive numbers
- [ ] Valid from dates are not in the past (or use current date)
- [ ] Currency codes are valid
- [ ] UOMs are valid
- [ ] No duplicate vendor-material-plant-purch org combinations

#### Post-Import Validation

**Step 1: Record Count**

- [ ] Count info records in S/4HANA
- [ ] Compare to source count

**Transaction Code:** `ME1M` (Info Record List)

**Step 2: Completeness Check**

- [ ] Display sample info records
- [ ] Verify prices loaded correctly
- [ ] Check lead times
- [ ] Verify validity dates

**Transaction Code:** `ME13` (Display Info Record)

**Step 3: Functional Testing**

- [ ] Create purchase requisition - verify info record is found
- [ ] Convert to purchase order - verify price from info record
- [ ] Check source determination uses info record

**Transaction Codes:**
- `ME51N` - Create PR
- `ME21N` - Create PO
- `ME03` - Source List

**Step 4: Integration with PPCA**

- [ ] Test PPCA workflow in BTP App
- [ ] Verify info record changes trigger approval
- [ ] Check approval routing

**Step 5: Reconciliation**

- [ ] Generate Info Record List
- [ ] Group by purchasing organization
- [ ] Verify coverage (% of materials with info records)
- [ ] Target: 95%+ coverage for regular procurement materials

**Transaction Code:** `ME1M` (Info Record List)

---

### Source Lists

**Object Details:**
- **Object ID:** 19
- **Source:** Manual/ECC
- **Dependencies:** Info Records
- **Complexity:** Low
- **Volume:** None in legacy (to be created)
- **Migration Tool:** MM_SOURCE_LIST template (Migration Cockpit)
- **Priority:** High
- **Estimated Duration:** 2-3 hours

#### Data Preparation & Cleansing

**Step 1: Define Source List Strategy**

- [ ] Determine which materials require source lists
- [ ] Identify fixed vendor assignments
- [ ] Define blocked sources (if any)
- [ ] Set vendor priority/ranking

**Step 2: Create Source List Data**

- [ ] For each material, list approved vendors
- [ ] Assign priority/ranking (1 = preferred)
- [ ] Set validity dates
- [ ] Flag MRP-relevant source
- [ ] Flag fixed source (if required)

**Step 3: Data Quality Checks**

- [ ] Verify material numbers exist
- [ ] Verify vendor numbers exist
- [ ] Check that info records exist for each vendor-material combination
- [ ] Validate date ranges
- [ ] Check priority assignments (no duplicates for same material)

**Step 4: Field Mapping**

| Source Field | S/4HANA Field | Transformation Rule |
|--------------|---------------|---------------------|
| Material Number | MATNR | Must exist in material master |
| Plant | WERKS | Must be valid |
| Vendor Number | LIFNR | Must exist in vendor master |
| Purchasing Organization | EKORG | Must match info record |
| Valid From | VALID_FROM | YYYY-MM-DD |
| Valid To | VALID_TO | YYYY-MM-DD or 12/31/9999 |
| MRP Indicator | MRP_IND | X = relevant for MRP |
| Fixed Vendor | FIXED_IND | X = fixed source |
| Blocked Source | BLOCK_IND | X = blocked |

#### Load Execution

**Step 1: Prepare File**

- [ ] Open MM_SOURCE_LIST template
- [ ] Enter source list entries
- [ ] Mandatory fields:
  - Material Number
  - Plant
  - Vendor
  - Valid From Date
- [ ] Save as: `WAVE2_SOURCE_LIST_[DATE]_V1.xlsx`

**Step 2: Load**

- [ ] Transaction `LTMC`
- [ ] Select "Source List"
- [ ] Create run: `SOURCE_LIST_LOAD_[DATE]`
- [ ] Upload file
- [ ] Execute

**Step 3: Key Parameters**

- [ ] Simulation Mode: Yes
- [ ] Commit Block Size: 200 records

#### Pre-Import Validation

- [ ] All materials exist
- [ ] All vendors exist
- [ ] Info records exist for all vendor-material combinations
- [ ] Valid from dates are logical
- [ ] No conflicting fixed sources for same material

#### Post-Import Validation

**Step 1: Record Count**

- [ ] Count source list records
- [ ] Compare to source

**Transaction Code:** `ME03` (Display Source List)

**Step 2: Functional Testing**

- [ ] Run MRP for material with source list
- [ ] Verify source determination uses source list
- [ ] Create purchase requisition - check vendor proposal
- [ ] Test source list in ME21N (create PO)

**Transaction Codes:**
- `MD04` - Stock/Requirements List
- `ME51N` - Create PR

**Step 3: Reconciliation**

- [ ] Generate source list report
- [ ] Verify all required materials have source lists
- [ ] Check that MRP indicator is set correctly

---

### Quota Arrangements

**Object Details:**
- **Object ID:** 20
- **Source:** ECC
- **Dependencies:** Source Lists
- **Complexity:** Low
- **Volume:** TBD
- **Migration Tool:** Manual/API
- **Priority:** Medium
- **Estimated Duration:** 2-3 hours

#### Data Preparation & Cleansing

**Step 1: Extract Quota Arrangement Data**

- [ ] Extract quota arrangements from ECC (if applicable)
- [ ] Identify materials that require quota arrangements
- [ ] Define quota splits (e.g., Vendor A: 60%, Vendor B: 40%)
- [ ] Set quota base quantity
- [ ] Define splitting rules

**Step 2: Data Quality Checks**

- [ ] Verify materials exist
- [ ] Verify all vendors in quota exist
- [ ] Check quota percentages sum to 100%
- [ ] Validate source lists exist
- [ ] Check validity periods

**Step 3: Field Mapping**

| Source Field | S/4HANA Field | Transformation Rule |
|--------------|---------------|---------------------|
| Material Number | MATNR | Must exist |
| Plant | WERKS | Must be valid |
| Vendor Number | LIFNR | Must exist |
| Quota Ranking | QUOTA_RANK | Sequence number |
| Quota Base Qty | QUOTA_BASE | Numeric |
| Quota | QUOTA_QTY | Numeric (percentage or quantity) |
| Valid From | VALID_FROM | YYYY-MM-DD |
| Valid To | VALID_TO | YYYY-MM-DD |

#### Load Execution

**Step 1: Manual Creation (if low volume)**

- [ ] Transaction `MEQ1` (Create Quota Arrangement)
- [ ] Enter material and plant
- [ ] Add vendors with quota splits
- [ ] Set validity dates
- [ ] Save

**Step 2: API Load (if high volume)**

- [ ] Prepare API payload with quota data
- [ ] Execute API call
- [ ] Validate response

**Step 3: Alternative - Excel Upload Program**

- [ ] Use custom upload program if available
- [ ] Prepare Excel file with quota data
- [ ] Execute upload program

#### Pre-Import Validation

- [ ] All materials exist
- [ ] All vendors exist
- [ ] Source lists exist for vendor-material combinations
- [ ] Quota percentages/quantities are valid
- [ ] Validity dates are logical

#### Post-Import Validation

**Step 1: Record Count**

- [ ] Count quota arrangements
- [ ] Compare to source

**Transaction Code:** `MEQ3` (Display Quota Arrangement)

**Step 2: Functional Testing**

- [ ] Run MRP for material with quota arrangement
- [ ] Verify quota split is respected in planning proposals
- [ ] Create multiple purchase requisitions to test quota distribution
- [ ] Check quota consumption

**Transaction Code:** `MD04` (Stock/Requirements List)

**Step 3: Reconciliation**

- [ ] Review quota arrangement report
- [ ] Verify quota splits are correct
- [ ] Check that quotas are consumed correctly

---

## 2.4 Production Master Data

### Bill of Materials (BOM)

**Object Details:**
- **Object ID:** 21
- **Source:** Manual
- **Dependencies:** Material Master
- **Complexity:** Medium
- **Volume:** TBD
- **Migration Tool:** BOM API / Upload Program
- **Priority:** Critical
- **Estimated Duration:** 6-10 hours

#### Data Preparation & Cleansing

**Step 1: Gather BOM Data**

- [ ] Extract BOM data from ECC (if applicable)
- [ ] Collect BOM information from manual sources (spreadsheets, documents)
- [ ] Identify all finished goods that require BOMs
- [ ] Map BOM structures (single-level and multi-level)
- [ ] Document component quantities and UOMs

**Step 2: Data Quality Checks**

- [ ] Verify all header materials (finished goods) exist in S/4HANA
- [ ] Verify all component materials exist in S/4HANA
- [ ] Check component quantities are positive
- [ ] Validate UOMs are correct (especially ZPC with 3 decimals)
- [ ] Check for circular BOM references (material using itself as component)
- [ ] Verify BOM alternative numbers (if multiple BOMs per material)
- [ ] Validate validity dates

**Step 3: Data Cleansing Rules**

- [ ] Standardize BOM item numbers (10, 20, 30...)
- [ ] Validate component quantities against production requirements
- [ ] Ensure UOM "ZPC" is used where required (with 3 decimal places)
- [ ] Remove obsolete BOM items
- [ ] Update component material numbers if changed

**Step 4: BOM Structure Definition**

| BOM Field | Description | Validation |
|-----------|-------------|------------|
| Material | Header material (finished good) | Must exist in material master |
| Plant | Production plant | Must be valid |
| BOM Alternative | Alternative BOM (usually 1) | Numeric |
| BOM Usage | Usage type (1=Production) | Must match configuration |
| Item Number | Component line item | 10, 20, 30... |
| Component | Component material number | Must exist in material master |
| Component Quantity | Quantity per header | Positive number |
| Component UOM | Unit of measure | Validate against UOM master |
| Component Scrap | Scrap percentage | 0-100% |
| Item Category | Item type (L=Stock item, N=Non-stock) | Must be valid |
| Valid From | Start date | YYYY-MM-DD |

**Step 5: Multi-Level BOM Handling**

For multi-level BOMs (finished good → sub-assembly → components):
- [ ] Create BOMs in bottom-up sequence (components first, then sub-assemblies, then finished goods)
- [ ] Validate that all sub-assemblies have their own BOMs before creating higher-level BOMs
- [ ] Test BOM explosion to verify multi-level structure

#### Load Execution

**Step 1: Prepare BOM Data File**

- [ ] Organize BOM data in hierarchical structure
- [ ] Create header records (one per BOM)
- [ ] Create item records (one per component)
- [ ] Include all mandatory fields:
  - Header: Material, Plant, BOM Usage, Alternative
  - Item: Item Number, Component, Quantity, UOM
- [ ] Save file as: `WAVE2_BOM_[DATE]_V1.xlsx` or CSV

**Step 2: Load Method Selection**

**Option A: Standard BOM Upload Program**
- [ ] Use transaction `CS01` to manually create BOMs (low volume only)
- [ ] Or use LSMW for BOM upload (medium volume)

**Option B: BOM API**
- [ ] Configure BOM API in S/4HANA
- [ ] Prepare API payload (JSON or XML)
- [ ] Test API with sample BOM
- [ ] Execute bulk API load

**Option C: Custom Upload Program**
- [ ] Use custom upload program if available
- [ ] Upload Excel file with BOM data
- [ ] Execute program

**Step 3: BOM Load Sequence**

Execute in this order:
1. [ ] Load single-level BOMs (finished goods with only purchased components)
2. [ ] Load sub-assembly BOMs (semi-finished goods)
3. [ ] Load multi-level BOMs (finished goods with sub-assemblies)

**Step 4: Execute Load**

**For Manual Creation (CS01):**
- [ ] Transaction `CS01`
- [ ] Enter material, plant, BOM usage
- [ ] Enter BOM alternative
- [ ] Add each component item
- [ ] Save

**For API Load:**
- [ ] Execute API call with BOM payload
- [ ] Monitor API response
- [ ] Check for errors in response
- [ ] Download API log

**For LSMW:**
- [ ] Execute LSMW project for BOM upload
- [ ] Map source file to BOM structure
- [ ] Run in test mode first
- [ ] Execute actual load

**Step 5: Error Resolution**

Common BOM errors:
- [ ] Header material not found - verify material master
- [ ] Component material not found - verify material master
- [ ] Invalid UOM - check UOM master (especially ZPC)
- [ ] Circular reference - review BOM structure
- [ ] BOM usage not valid - check configuration
- [ ] Plant not valid - verify plant in material master

#### Pre-Import Validation

- [ ] All header materials exist in material master
- [ ] All component materials exist in material master
- [ ] Component quantities are positive
- [ ] UOMs are valid (ZPC configured with 3 decimals)
- [ ] No circular BOM references
- [ ] BOM alternatives are unique per material-plant
- [ ] Item numbers are sequential (10, 20, 30...)
- [ ] Multi-level BOM structure is logical (no missing sub-assemblies)

#### Post-Import Validation

**Step 1: Record Count**

- [ ] Count total BOMs created
- [ ] Count by material type (finished goods, semi-finished goods)
- [ ] Compare to source count

**Transaction Code:** `CS03` (Display BOM)

**Step 2: BOM Structure Validation**

- [ ] Open sample BOMs in CS03
- [ ] Verify all components are listed
- [ ] Check component quantities
- [ ] Verify UOMs (especially ZPC with 3 decimals)
- [ ] Review BOM header data (usage, alternative)
- [ ] Check 20% sample of BOMs

**Transaction Code:** `CS03` (Display BOM)

**Step 3: Multi-Level BOM Explosion**

- [ ] Execute BOM explosion for multi-level BOMs
- [ ] Verify all levels are correctly structured
- [ ] Check component summary (total quantity across all levels)
- [ ] Validate sub-assembly BOMs explode correctly

**Transaction Code:** `CS12` (BOM Explosion / BOM List)

**Step 4: Functional Testing**

- [ ] **Production Order Test:**
  - Create planned order for finished good with BOM
  - Verify component requirements are generated
  - Check component quantities match BOM
- [ ] **MRP Test:**
  - Run MRP for finished goods
  - Verify dependent requirements created for components
  - Check quantity calculations
- [ ] **Costing Test:**
  - Run cost estimate for material with BOM
  - Verify component costs are included
  - Check cost roll-up for multi-level BOMs

**Transaction Codes:**
- `MD01` - MRP Run
- `MD04` - Stock/Requirements List
- `CK11N` - Create Standard Cost Estimate

**Step 5: System Validation**

- [ ] Test BOM change functionality (CS02)
- [ ] Verify BOM history is maintained
- [ ] Check BOM status is active
- [ ] Validate BOM validity dates

**Transaction Code:** `CS02` (Change BOM)

**Step 6: Integration Testing**

- [ ] Test BOM usage in production planning
- [ ] Verify BOM appears in material master PP view
- [ ] Check BOM explosion in sales order (if configurable products)
- [ ] Validate BOM in costing

**Step 7: Reconciliation Report**

- [ ] Generate BOM Where-Used List for components
- [ ] Generate BOM List for all finished goods
- [ ] Compare to source BOM data
- [ ] Document any missing or additional BOMs
- [ ] Verify all active finished goods have BOMs

**Transaction Codes:**
- `CS15` - BOM Where-Used List
- `CS12` - BOM List

---

## 2.5 Sales Master Data

### Customer Pricing Conditions

**Object Details:**
- **Object ID:** 22
- **Source:** ECC
- **Dependencies:** Customers, Materials
- **Complexity:** Low
- **Volume:** TBD
- **Migration Tool:** SD_PRICING template (Migration Cockpit)
- **Priority:** High
- **Estimated Duration:** 3-4 hours

#### Data Preparation & Cleansing

**Step 1: Extract Pricing Data from ECC**

- [ ] Extract customer-specific pricing from ECC
- [ ] Extract pricing conditions (PR00 - Price, K004 - Material Discount, etc.)
- [ ] Include validity dates
- [ ] Extract pricing scales (if applicable)
- [ ] Gather sales organization and distribution channel data

**Step 2: Data Quality Checks**

- [ ] Verify all customers exist in S/4HANA
- [ ] Verify all materials exist in S/4HANA (if material-specific pricing)
- [ ] Check pricing condition types are configured in S/4HANA
- [ ] Validate price amounts are positive
- [ ] Check currency codes
- [ ] Verify validity dates (remove expired conditions)
- [ ] Check pricing scales are correct

**Step 3: Data Cleansing Rules**

- [ ] Remove expired pricing conditions (valid to date in past)
- [ ] Update customer numbers if changed in S/4HANA
- [ ] Update material numbers if changed in S/4HANA
- [ ] Standardize currency codes
- [ ] Validate condition types match S/4HANA pricing procedure

**Step 4: Field Mapping**

| ECC Field | S/4HANA Field | Transformation Rule |
|-----------|---------------|---------------------|
| KUNNR | Customer Number | Must exist in customer master |
| MATNR | Material Number | Must exist (if material-specific) |
| KSCHL | Condition Type | Must be configured (PR00, K004, etc.) |
| VKORG | Sales Organization | Must be valid |
| VTWEG | Distribution Channel | Must be valid |
| KBETR | Condition Value | Price amount |
| KONWA | Condition Currency | ISO currency code |
| KPEIN | Pricing Unit | Numeric |
| KMEIN | Unit of Measure | Validate against UOM master |
| DATAB | Valid From | YYYY-MM-DD |
| DATBI | Valid To | YYYY-MM-DD |

#### Load Execution

**Step 1: Prepare File**

- [ ] Open SD_PRICING template
- [ ] Copy pricing condition data
- [ ] Mandatory fields:
  - Customer (or Customer + Material for material-specific)
  - Condition Type
  - Sales Organization
  - Condition Value
  - Currency
  - Valid From
- [ ] Save as: `WAVE2_PRICING_[DATE]_V1.xlsx`

**Step 2: Load**

- [ ] Transaction `LTMC`
- [ ] Select "SD Pricing Conditions"
- [ ] Create run: `PRICING_LOAD_[DATE]`
- [ ] Upload file
- [ ] Execute

**Step 3: Key Parameters**

- [ ] Simulation Mode: Yes
- [ ] Commit Block Size: 100 records

#### Pre-Import Validation

- [ ] All customers exist
- [ ] All materials exist (if material-specific pricing)
- [ ] Condition types are configured
- [ ] Currency codes are valid
- [ ] Validity dates are logical
- [ ] No overlapping pricing conditions for same customer-material combination

#### Post-Import Validation

**Step 1: Record Count**

- [ ] Count pricing conditions loaded
- [ ] Compare to source

**Transaction Code:** `VK13` (Display Pricing Condition)

**Step 2: Completeness Check**

- [ ] Display sample pricing conditions in VK13
- [ ] Verify condition values are correct
- [ ] Check validity dates
- [ ] Review pricing scales (if applicable)

**Step 3: Functional Testing**

- [ ] Create test sales order for customer with pricing
- [ ] Verify pricing condition is determined
- [ ] Check price calculation in sales order
- [ ] Test discounts and surcharges

**Transaction Code:** `VA01` (Create Sales Order)

**Step 4: Pricing Simulation**

- [ ] Run pricing simulation for sample customers
- [ ] Verify all pricing elements are included
- [ ] Check condition values match expected

**Transaction Code:** `VA01` (use pricing analysis button)

**Step 5: Reconciliation**

- [ ] Generate pricing condition report
- [ ] Compare to ECC pricing conditions
- [ ] Verify all active conditions migrated
- [ ] Document any exclusions

---

### Credit Accounts

**Object Details:**
- **Object ID:** 23
- **Source:** ECC
- **Dependencies:** Customers
- **Complexity:** Low
- **Volume:** TBD
- **Migration Tool:** Manual Configuration
- **Priority:** Medium
- **Estimated Duration:** 2-3 hours

#### Data Preparation & Cleansing

**Step 1: Extract Credit Data**

- [ ] Extract customer credit limits from ECC
- [ ] Extract credit control area assignments
- [ ] Get credit exposure data
- [ ] Identify credit blocked customers
- [ ] Gather credit terms and payment behavior data

**Step 2: Data Quality Checks**

- [ ] Verify all customers exist in S/4HANA
- [ ] Validate credit control area is configured
- [ ] Check credit limit amounts are reasonable
- [ ] Verify currency codes

**Step 3: Field Mapping**

| ECC Field | S/4HANA Field | Transformation Rule |
|-----------|---------------|---------------------|
| KUNNR | Customer | Must exist |
| KKBER | Credit Control Area | Must be configured |
| KLIMK | Credit Limit | Numeric |
| WAERS | Currency | ISO currency code |
| CTLPC | Credit Limit % | Percentage (0-100) |
| GRUPP | Risk Category | Map to S/4HANA risk categories |

#### Load Execution

**Step 1: Manual Configuration**

For each customer requiring credit management:
- [ ] Transaction `FD32` (Change Customer Credit Management)
- [ ] Enter customer number
- [ ] Enter credit control area
- [ ] Enter credit limit
- [ ] Set risk category
- [ ] Save

**Step 2: Bulk Update (if available)**

- [ ] Use custom program or LSMW for bulk credit limit update
- [ ] Prepare file with customer, credit control area, credit limit
- [ ] Execute upload

#### Pre-Import Validation

- [ ] All customers exist
- [ ] Credit control area is configured
- [ ] Credit limits are positive numbers
- [ ] Currency codes are valid

#### Post-Import Validation

**Step 1: Record Count**

- [ ] Count customers with credit management data
- [ ] Compare to source

**Transaction Code:** `FD33` (Display Customer Credit Management)

**Step 2: Functional Testing**

- [ ] Create sales order for customer with credit limit
- [ ] Verify credit check is triggered
- [ ] Test credit block when limit exceeded
- [ ] Check credit exposure calculation

**Transaction Code:** `VA01` (Create Sales Order)

**Step 3: Reconciliation**

- [ ] Generate customer credit report
- [ ] Compare to ECC
- [ ] Verify all credit limits migrated

---

### Customer Material Info

**Object Details:**
- **Object ID:** 24
- **Source:** ECC
- **Dependencies:** Customers, Materials
- **Complexity:** Low
- **Volume:** TBD
- **Migration Tool:** SD_CUST_MATERIAL template (Migration Cockpit)
- **Priority:** Medium
- **Estimated Duration:** 2-3 hours

#### Data Preparation & Cleansing

**Step 1: Extract Customer Material Info**

- [ ] Extract customer material info records from ECC
- [ ] Get customer-specific material numbers
- [ ] Get customer material descriptions
- [ ] Extract any customer-specific data (delivery plant, etc.)

**Step 2: Data Quality Checks**

- [ ] Verify all customers exist in S/4HANA
- [ ] Verify all materials exist in S/4HANA
- [ ] Check customer material numbers are not duplicates
- [ ] Validate sales organizations

**Step 3: Field Mapping**

| ECC Field | S/4HANA Field | Transformation Rule |
|-----------|---------------|---------------------|
| KUNNR | Customer | Must exist |
| MATNR | Material | Must exist |
| KDMAT | Customer Material | Customer's material number |
| VKORG | Sales Organization | Must be valid |
| VTWEG | Distribution Channel | Must be valid |

#### Load Execution

**Step 1: Prepare File**

- [ ] Open SD_CUST_MATERIAL template
- [ ] Enter customer material info data
- [ ] Save as: `WAVE2_CUST_MATERIAL_[DATE]_V1.xlsx`

**Step 2: Load**

- [ ] Transaction `LTMC`
- [ ] Select "Customer Material Info"
- [ ] Create run: `CUST_MATERIAL_LOAD_[DATE]`
- [ ] Upload file
- [ ] Execute

#### Pre-Import Validation

- [ ] All customers exist
- [ ] All materials exist
- [ ] Sales organizations are valid
- [ ] No duplicate customer material numbers for same customer

#### Post-Import Validation

**Step 1: Record Count**

- [ ] Count customer material info records
- [ ] Compare to source

**Transaction Code:** `VD53` (Display Customer Material Info)

**Step 2: Functional Testing**

- [ ] Create sales order using customer material number
- [ ] Verify system finds correct material
- [ ] Test customer material search in sales order

**Transaction Code:** `VA01` (Create Sales Order)

**Step 3: Reconciliation**

- [ ] Generate customer material info report
- [ ] Compare to ECC
- [ ] Verify all records migrated

---

## Wave 2 Load Sequence

Execute Wave 2 objects in the following sequence, respecting dependencies:

### Phase 1: Business Partners (Day 1-2)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 1.1 | BP - Vendors | BP_VENDOR template | 6-8 hrs | GL Accounts, Payment Terms, Bank Master (Wave 1) | [ ] |
| 1.2 | BP - Customers | BP_CUSTOMER template | 4-6 hrs | GL Accounts, Payment Terms (Wave 1) | [ ] |

**Phase 1 Checkpoint:**
- [ ] All vendors loaded and validated
- [ ] All customers loaded and validated
- [ ] Reconciliation reports reviewed and signed off
- [ ] No critical errors remaining

### Phase 2: Material Master (Day 2-3)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 2.1 | Material Master | MM_MATERIAL_MASTER / API | 8-12 hrs | GL Accounts, Material Groups (Wave 1) | [ ] |

**Phase 2 Checkpoint:**
- [ ] All materials loaded and validated
- [ ] All material views complete (MRP, Purchasing, Sales, Accounting)
- [ ] Integration with Smart-Fulfillment System tested
- [ ] Material master reconciliation complete

### Phase 3: Procurement Master Data (Day 3-4)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 3.1 | Purchasing Info Records | MM_INFO_RECORD template | 4-6 hrs | Vendors (1.1), Materials (2.1) | [ ] |
| 3.2 | Source Lists | MM_SOURCE_LIST template | 2-3 hrs | Info Records (3.1) | [ ] |
| 3.3 | Quota Arrangements | Manual/API | 2-3 hrs | Source Lists (3.2) | [ ] |

**Phase 3 Checkpoint:**
- [ ] Info records loaded and validated
- [ ] Source lists loaded and validated
- [ ] Quota arrangements loaded (if applicable)
- [ ] Procurement setup complete and tested

### Phase 4: Production Master Data (Day 4-5)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 4.1 | Bill of Materials (BOM) | BOM API / Upload Program | 6-10 hrs | Material Master (2.1) | [ ] |

**Phase 4 Checkpoint:**
- [ ] All BOMs loaded and validated
- [ ] Multi-level BOM structures tested
- [ ] BOM explosion verified
- [ ] Special UOM "ZPC" with 3 decimals confirmed

### Phase 5: Sales Master Data (Day 5-6)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 5.1 | Customer Pricing Conditions | SD_PRICING template | 3-4 hrs | Customers (1.2), Materials (2.1) | [ ] |
| 5.2 | Credit Accounts | Manual Configuration | 2-3 hrs | Customers (1.2) | [ ] |
| 5.3 | Customer Material Info | SD_CUST_MATERIAL template | 2-3 hrs | Customers (1.2), Materials (2.1) | [ ] |

**Phase 5 Checkpoint:**
- [ ] Pricing conditions loaded and validated
- [ ] Credit management configured
- [ ] Customer material info loaded
- [ ] Sales setup complete and tested

### Phase 6: Final Validation & Sign-Off (Day 6-7)

| Step | Activity | Duration | Status |
|------|----------|----------|--------|
| 6.1 | End-to-end integration testing | 4 hrs | [ ] |
| 6.2 | Complete all validation checklists | 2 hrs | [ ] |
| 6.3 | Generate final reconciliation reports | 2 hrs | [ ] |
| 6.4 | Functional sign-off by all leads | 1 hr | [ ] |
| 6.5 | Wave 2 completion documentation | 1 hr | [ ] |

---

## Validation & Sign-Off Checklist

### Business Partner Validation

#### Vendor Master Validation
- [ ] Total vendor count reconciles (S/4HANA = ECC)
- [ ] Vendor reconciliation accounts are correct
- [ ] Vendor payment terms are correct
- [ ] Vendor bank details are complete
- [ ] Vendor purchasing data is complete
- [ ] Number ranges are correctly assigned (Z001, Z002, ZEMP, ZCPD)
- [ ] Inter-company vendors are flagged
- [ ] Sample purchase order creation successful
- [ ] Vendor search functionality works
- [ ] No duplicate vendor records

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______

#### Customer Master Validation
- [ ] Total customer count reconciles (S/4HANA = ECC)
- [ ] Customer reconciliation accounts are correct
- [ ] Customer payment terms are correct
- [ ] Customer sales area data is complete
- [ ] Customer credit control area assignments correct
- [ ] Sample sales order creation successful
- [ ] Customer search functionality works
- [ ] Pricing conditions are determined correctly
- [ ] No duplicate customer records

**Sign-Off:**
- [ ] SD Lead: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______

### Material Master Validation

- [ ] Total material count reconciles
- [ ] All material types represented (ZFER, ZH01-ZH44, ZHL1-ZHL2)
- [ ] Material descriptions are complete
- [ ] Base UOM is correct for all materials
- [ ] Special UOM "ZPC" configured with 3 decimals
- [ ] Material valuation classes are correct
- [ ] MRP views are complete
- [ ] Purchasing views are complete
- [ ] Sales views are complete (for saleable materials)
- [ ] Accounting views are complete
- [ ] Profit center assignments correct (if used)
- [ ] Material groups assigned correctly
- [ ] GL account determination works correctly
- [ ] Integration with Smart-Fulfillment System successful
- [ ] Sample material search works
- [ ] Sample MRP run successful
- [ ] Sample PO creation with materials successful

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______
- [ ] PP Lead: _________________ Date: _______
- [ ] SD Lead: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______

### Procurement Master Data Validation

#### Info Records
- [ ] Info record count documented
- [ ] Coverage: 95%+ of regular procurement materials have info records
- [ ] Prices are correct
- [ ] Lead times are reasonable
- [ ] Minimum order quantities correct
- [ ] Info records appear in PO creation
- [ ] PPCA workflow tested (BTP App)

#### Source Lists
- [ ] Source list count documented
- [ ] All required materials have source lists
- [ ] MRP uses source lists correctly
- [ ] Vendor proposals in PR creation are correct

#### Quota Arrangements
- [ ] Quota arrangements count documented
- [ ] Quota splits are correct
- [ ] MRP respects quota arrangements
- [ ] Quota consumption is tracked

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______

### Production Master Data Validation

#### Bill of Materials (BOM)
- [ ] BOM count reconciles
- [ ] All finished goods have BOMs
- [ ] Component quantities are correct
- [ ] UOM "ZPC" with 3 decimals works correctly
- [ ] Multi-level BOMs explode correctly
- [ ] BOM explosion (CS12) successful
- [ ] Dependent requirements generated in MRP
- [ ] Cost roll-up works for multi-level BOMs
- [ ] No circular BOM references
- [ ] BOM where-used list accurate

**Sign-Off:**
- [ ] PP Lead: _________________ Date: _______

### Sales Master Data Validation

#### Pricing Conditions
- [ ] Pricing condition count documented
- [ ] Customer-specific pricing works correctly
- [ ] Material-specific pricing works correctly
- [ ] Discounts and surcharges apply correctly
- [ ] Pricing scales work (if applicable)
- [ ] Pricing in sales orders is correct

#### Credit Management
- [ ] Credit limits are set correctly
- [ ] Credit checks trigger in sales orders
- [ ] Credit blocks work when limit exceeded
- [ ] Credit exposure calculation is correct

#### Customer Material Info
- [ ] Customer material info count documented
- [ ] Customer material numbers work in sales orders
- [ ] Material search by customer material number works

**Sign-Off:**
- [ ] SD Lead: _________________ Date: _______

### Integration Testing

- [ ] End-to-end procurement process tested (PR → PO → GR → Invoice)
- [ ] End-to-end sales process tested (SO → Delivery → Invoice)
- [ ] End-to-end production process tested (Planned Order → Production → GR)
- [ ] MRP run successful with all master data
- [ ] Costing run successful (materials with BOMs)
- [ ] Smart-Fulfillment System integration tested
- [ ] Reporting data available for all master data

**Sign-Off:**
- [ ] Integration Lead: _________________ Date: _______

### Final Wave 2 Sign-Off

- [ ] All 10 Wave 2 objects loaded successfully
- [ ] All validation checklists complete
- [ ] All reconciliation reports reviewed
- [ ] All functional testing passed
- [ ] No critical errors remaining
- [ ] All error logs reviewed and resolved
- [ ] All functional leads have signed off
- [ ] Wave 2 completion documentation complete
- [ ] Ready to proceed to Wave 3

**Overall Wave 2 Sign-Off:**
- [ ] Data Migration Lead: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______
- [ ] MM Lead: _________________ Date: _______
- [ ] SD Lead: _________________ Date: _______
- [ ] PP Lead: _________________ Date: _______
- [ ] Project Manager: _________________ Date: _______

---

## Troubleshooting Reference

### Common Issues & Resolutions

#### Business Partner Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Vendor load fails - "Reconciliation account not found" | GL account doesn't exist or not configured for vendor account group | Verify GL account in FI master; Update vendor account group configuration | FI Lead |
| Customer load fails - "Sales area not found" | Sales org/distribution channel not configured | Configure sales area in IMG; Verify customer sales area data | SD Lead |
| Duplicate business partner error | Business partner number already exists | Check for existing BP; Use different number or update existing | MM/SD Lead |
| Bank details not accepted | Bank key not found in Bank Master | Load bank master first (Wave 1); Verify bank country and bank key | FI Lead |
| Tax ID validation error | Tax ID format incorrect for country | Check tax ID format for each country; Update source data | FI Lead |

#### Material Master Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Material load fails - "Material type not found" | Material type not configured | Configure material type in IMG; Verify material type code | MM Lead |
| Material load fails - "Valuation class not assigned to material type" | Valuation class not linked to material type | Assign valuation class to material type in configuration | FI/MM Lead |
| UOM error - "ZPC not found" | Special UOM not created | Create UOM "ZPC" with 3 decimal places; Test conversion | MM Lead |
| Material group not found | Material group not configured | Create material group in IMG; Update material data | MM Lead |
| Profit center derivation error | Profit center not assigned or invalid | Verify profit center master; Update material accounting view | FI/CO Lead |
| GL account determination fails | Account determination not configured for valuation class | Configure account determination for material type and valuation class | FI Lead |

#### Procurement Master Data Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Info record load fails - "Vendor not found" | Vendor doesn't exist in S/4HANA | Load vendor master first; Verify vendor number | MM Lead |
| Info record load fails - "Material not found" | Material doesn't exist in S/4HANA | Load material master first; Verify material number | MM Lead |
| Info record not appearing in PO | Purchasing organization or plant mismatch | Verify info record org data matches PO org data; Check validity dates | MM Lead |
| Source list not used by MRP | MRP indicator not set | Set MRP indicator in source list; Re-run MRP | PP/MM Lead |
| Quota arrangement error | Source list missing or incorrect | Create source list first; Verify vendor-material combination | MM Lead |

#### BOM Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| BOM load fails - "Material not found" | Header or component material doesn't exist | Load material master first; Verify material numbers | PP Lead |
| BOM load fails - "UOM not found" | Component UOM not valid | Verify UOM master; Check UOM for component material | MM Lead |
| BOM explosion error | Circular BOM reference or missing sub-assembly BOM | Check BOM structure for loops; Create missing sub-assembly BOMs | PP Lead |
| BOM not used in MRP | BOM not active or usage type incorrect | Check BOM status; Verify BOM usage = 1 (Production) | PP Lead |
| Component quantity incorrect | Data entry error or UOM mismatch | Review BOM component quantities; Check UOM conversion | PP Lead |
| Multi-level BOM incomplete | Sub-assembly BOMs not created | Create BOMs in bottom-up sequence (components first) | PP Lead |

#### Sales Master Data Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Pricing condition not determined | Condition type not in pricing procedure or condition record missing | Verify pricing procedure configuration; Check condition record validity | SD Lead |
| Credit check not triggered | Credit control area not assigned to customer | Assign credit control area in customer master; Configure credit check | SD/FI Lead |
| Customer material number not working | Customer material info not loaded or sales org mismatch | Load customer material info; Verify sales org in record | SD Lead |

### Escalation Path

| Level | Contact | Response Time | Issues Handled |
|-------|---------|---------------|----------------|
| **Level 1: Technical Team** | Migration Team Members | Immediate | Data errors, file format issues, standard migration errors |
| **Level 2: Functional Leads** | FI/MM/SD/PP Leads | 1-2 hours | Configuration issues, business logic validation, functional testing failures |
| **Level 3: Project Manager** | Project Manager | 2-4 hours | Resource issues, timeline delays, cross-functional dependencies |
| **Level 4: Executive Sponsor** | Executive Sponsor | 4-8 hours | Critical blockers, go/no-go decisions, major scope changes |

### Key Contacts

| Role | Name | Email | Phone | Availability |
|------|------|-------|-------|--------------|
| Data Migration Lead | TBD | TBD | TBD | 24/7 during migration window |
| FI Lead | Frey Zheng | TBD | TBD | Business hours + on-call |
| MM Lead | Meos Xu | TBD | TBD | Business hours + on-call |
| SD Lead | Warner Yu | TBD | TBD | Business hours + on-call |
| PP Lead | Joe Wu | TBD | TBD | Business hours + on-call |
| Project Manager | TBD | TBD | TBD | Business hours + on-call |
| SAP Basis Support | TBD | TBD | TBD | 24/7 |

### Useful Transaction Codes

#### Business Partner
- `BP` - Business Partner Master
- `XK03` - Display Vendor (Central)
- `FK03` - Display Vendor (Company Code)
- `MK03` - Display Vendor (Purchasing)
- `XD03` - Display Customer (Central)
- `FD03` - Display Customer (Company Code)
- `VD03` - Display Customer (Sales)

#### Material Master
- `MM03` - Display Material
- `MM60` - Material List
- `MMBE` - Stock Overview
- `MB52` - Stock List

#### Procurement
- `ME13` - Display Info Record
- `ME1M` - Info Record List
- `ME03` - Display Source List
- `MEQ3` - Display Quota Arrangement
- `ME51N` - Create Purchase Requisition
- `ME21N` - Create Purchase Order

#### Production
- `CS03` - Display BOM
- `CS12` - BOM Explosion
- `CS15` - BOM Where-Used List
- `MD01` - MRP Run
- `MD04` - Stock/Requirements List

#### Sales
- `VK13` - Display Pricing Condition
- `VA01` - Create Sales Order
- `VD53` - Display Customer Material Info
- `FD33` - Display Customer Credit Management

#### Migration
- `LTMC` - Migration Cockpit
- `LTMOM` - Migration Object Modeler
- `SLG1` - Application Log

#### System
- `SM37` - Job Overview
- `SM50` - Process Overview
- `SE16` - Data Browser

---

## Document Control

**Version History:**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | TBD | Data Migration Team | Initial version |

**Approval:**

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Data Migration Lead | TBD | | |
| FI Lead | Frey Zheng | | |
| MM Lead | Meos Xu | | |
| SD Lead | Warner Yu | | |
| PP Lead | Joe Wu | | |
| Project Manager | TBD | | |

---

**End of Wave 2 Execution Runbook**

