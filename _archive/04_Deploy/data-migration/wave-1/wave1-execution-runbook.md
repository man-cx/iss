# Wave 1 Data Migration Execution Runbook
**SAP ECC to S/4HANA Cloud - Home Control**

**Document Version:** 1.0  
**Wave:** 1 - Foundation Master Data  
**Date:** November 2025  
**Timing:** T-4 weeks before Go-Live  
**Duration:** 3-5 days  
**Objects Covered:** 14 foundation objects

---

## Table of Contents

1. [Pre-Migration Activities](#pre-migration-activities)
2. [Execution Procedures by Object](#execution-procedures-by-object)
   - [1.1 Organizational Structure](#11-organizational-structure)
     - [Object 1: Chart of Accounts](#object-1-chart-of-accounts)
     - [Object 2: Company Code Structure](#object-2-company-code-structure)
   - [1.2 FI Foundation](#12-fi-foundation)
     - [Object 3: GL Account Master](#object-3-gl-account-master)
     - [Object 4: Bank Master Data](#object-4-bank-master-data)
     - [Object 5: Tax Codes](#object-5-tax-codes)
     - [Object 6: Payment Terms](#object-6-payment-terms)
   - [1.3 CO Foundation](#13-co-foundation)
     - [Object 7: Cost Center Master](#object-7-cost-center-master)
     - [Object 8: Cost Center Hierarchy](#object-8-cost-center-hierarchy)
     - [Object 9: Profit Center Master](#object-9-profit-center-master)
     - [Object 10: Profit Center Hierarchy](#object-10-profit-center-hierarchy)
     - [Object 11: Primary Cost Elements](#object-11-primary-cost-elements)
     - [Object 12: Secondary Cost Elements](#object-12-secondary-cost-elements)
     - [Object 13: Statistical Key Figures](#object-13-statistical-key-figures)
   - [1.4 Asset Accounting](#14-asset-accounting)
     - [Object 14: Fixed Asset Master](#object-14-fixed-asset-master)
3. [Wave 1 Load Sequence](#wave-1-load-sequence)
4. [Validation & Sign-Off Checklist](#validation--sign-off-checklist)
5. [Troubleshooting Quick Reference](#troubleshooting-quick-reference)

---

## Pre-Migration Activities

### System Readiness Checks

**S/4HANA Environment:**
- [ ] Sandbox/Development system is available and accessible
- [ ] System has been configured with basic settings (system parameters, number ranges)
- [ ] Sufficient storage space for migration files and logs
- [ ] System performance baseline established

**ECC Source System:**
- [ ] Source data extraction access confirmed
- [ ] Data freeze communication sent (if applicable for Wave 1)
- [ ] Backup of source data completed

### User Access Verification

**Required Authorizations:**
- [ ] Migration Cockpit access (transaction LTMC or LTMOM)
- [ ] Configuration transaction access (SPRO, OB52, OKP1, etc.)
- [ ] Master data creation roles (FI_MASTER_MAINTAIN, CO_MASTER_MAINTAIN)
- [ ] File upload/download permissions
- [ ] Display and reporting authorizations

**Team Access:**
- [ ] FI Lead has required access
- [ ] CO Lead has required access
- [ ] Technical migration lead has full access
- [ ] All team members can access shared migration folder

### Template Downloads and Preparation

**Migration Cockpit Templates:**
- [ ] Download FI_GL_ACCOUNT template from LTMC
- [ ] Download FI_BANK template from LTMC
- [ ] Download CO_COST_CENTER template from LTMC
- [ ] Download CO_PROFIT_CENTER template from LTMC
- [ ] Download FI_ASSET_MASTER template from LTMC

**File Preparation:**
- [ ] Create working folder structure: `/wave1/source/`, `/wave1/staging/`, `/wave1/loaded/`
- [ ] Prepare Excel templates for manual configuration items
- [ ] Set up validation tracking spreadsheet

### Source Data Extraction from ECC

**Extraction Queries/Programs:**
- [ ] Extract Chart of Accounts (table SKA1, T004)
- [ ] Extract Company Code details (table T001)
- [ ] Extract GL Account Master (tables SKA1, SKB1, SKAT)
- [ ] Extract Bank Master (tables BNKA, T012, T012K)
- [ ] Extract Tax Codes (tables T007A, T007S)
- [ ] Extract Payment Terms (table T052)
- [ ] Extract Cost Centers (tables CSKS, CSKT)
- [ ] Extract Cost Center Hierarchy (table SETNODE, SETHEADER)
- [ ] Extract Profit Centers (tables CEPC, CEPCT)
- [ ] Extract Profit Center Hierarchy (table SETNODE, SETHEADER)
- [ ] Extract Secondary Cost Elements (table CSKU)
- [ ] Extract Statistical Key Figures (table TKA02)
- [ ] Extract Fixed Asset Master (tables ANLA, ANLB, ANLC, ANLZ)

---

## Execution Procedures by Object

### 1.1 Organizational Structure

#### Object 1: Chart of Accounts

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: OB13 (Display Chart of Accounts)
- Tables: SKA1, T004
- Extract Fields: KTOPL (CoA), KTPLT (Description), KTOPL_FLAG (Flag)
- Expected Records: 1 (YCOA)

*Data Quality Checks:*
- [ ] Verify Chart of Accounts code = YCOA
- [ ] Confirm description is complete
- [ ] Check no duplicate entries
- [ ] Validate language settings (EN, ZH if needed)

*Cleansing Rules:*
- No transformation needed - direct configuration in S/4HANA

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| KTOPL | Chart of Accounts | Direct |
| KTPLT | Description | Direct |

**Load Execution:**

*Migration Tool:* Manual Configuration

*Load Steps:*
1. Log into S/4HANA system
2. Transaction: OB13 (Chart of Accounts)
3. Create new Chart of Accounts: YCOA
4. Enter description: "Home Control Chart of Accounts"
5. Set language: EN (default)
6. Save configuration

*Key Configuration Parameters:*
- Chart of Accounts: YCOA
- Length of GL Account: 10 digits (SAP default)
- Group Chart of Accounts: (blank or YCOA)

**Pre-Import Validation:**

- [ ] Verify Chart of Accounts code = YCOA in source data
- [ ] Confirm description is complete
- [ ] Check no duplicate entries
- [ ] Validate language settings (EN, ZH if needed)

**Post-Import Validation:**

- [ ] Chart of Accounts YCOA exists in S/4HANA (via OB13)
- [ ] Description displays correctly
- [ ] Can be assigned to Company Codes
- [ ] No error messages in configuration log
- [ ] Available for GL account assignment

---

#### Object 2: Company Code Structure

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: OX02 (Display Company Code)
- Table: T001
- Extract Fields: BUKRS, BUTXT, WAERS, ORT01, LAND1, etc.
- Expected Records: 7 (SG21, CN13, CN17, US10, BE10, HCIL, BR10)

*Data Quality Checks:*
- [ ] All 7 company codes present
- [ ] Currency codes valid (SGD, CNY, USD, EUR, KYD, BRL)
- [ ] Country codes valid
- [ ] Fiscal year variant = K4 for all
- [ ] Chart of Accounts = YCOA for all

*Cleansing Rules:*
- Standardize address format
- Validate tax registration numbers
- Ensure all mandatory fields populated

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BUKRS | Company Code | Direct |
| BUTXT | Company Name | Direct |
| WAERS | Currency | Direct |
| PERIV | Fiscal Year Variant | Direct (K4) |
| KTOPL | Chart of Accounts | Direct (YCOA) |

**Load Execution:**

*Migration Tool:* Migration Cockpit (LTMC)

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: Company Code (or create custom object)
3. Create migration project: "WAVE1_COMPCODE"
4. Upload prepared file with 7 company codes
5. Execute field mapping validation
6. Simulate migration
7. Review simulation log
8. Execute final migration
9. Monitor processing log

*File Format:* CSV or Excel with columns:
- Company Code, Company Name, Currency, City, Country, Fiscal Year Variant, Chart of Accounts

*Key Configuration Parameters:*
- Batch size: All 7 in single batch
- Error handling: Stop on critical errors
- Duplicate check: Active

**Pre-Import Validation:**

- [ ] All 7 company codes present in source file
- [ ] Currency codes valid (SGD, CNY, USD, EUR, KYD, BRL)
- [ ] Country codes valid
- [ ] Fiscal year variant = K4 for all
- [ ] Chart of Accounts = YCOA for all
- [ ] Address format standardized
- [ ] All mandatory fields populated

**Post-Import Validation:**

- [ ] All 7 company codes created successfully in S/4HANA
- [ ] Each company code assigned to Chart of Accounts YCOA
- [ ] Currency and fiscal year variant correct per company code
- [ ] Can access company code via transaction OX03 or FS00
- [ ] Company code assignments ready for next objects
- [ ] Record count: 7 created = 7 expected

---

### 1.2 FI Foundation

#### Object 3: GL Account Master

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: FS00 (GL Account Master Display)
- Tables: SKA1 (Chart of Accounts data), SKB1 (Company Code data), SKAT (GL Account texts)
- Extract Fields: SAKNR, TXT50, XBILK, KTOKS, reconciliation account indicators
- Expected Records: ~1,000 GL accounts

*Data Quality Checks:*
- [ ] No duplicate GL account numbers
- [ ] All GL accounts have descriptions
- [ ] Account groups (KTOKS) are valid
- [ ] Balance sheet/P&L indicator set correctly
- [ ] Reconciliation account flags appropriate for vendor/customer/asset accounts
- [ ] Cost element indicators match CO requirements

*Cleansing Rules:*
- Remove inactive/blocked accounts (or flag for exclusion)
- Standardize account descriptions (max length 50 characters)
- Map ECC account groups to S/4HANA account groups
- Validate posting block indicators
- Ensure company code assignments complete for all 7 entities

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| SAKNR | G/L Account Number | Direct |
| TXT50 | G/L Account Short Text | Direct |
| XBILK | Balance Sheet Account | Direct |
| KTOKS | G/L Account Group | Map to S/4 groups |
| WAERS | Account Currency | Direct |

**Load Execution:**

*Migration Tool:* Migration Cockpit - FI_GL_ACCOUNT template

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: FI_GL_ACCOUNT
3. Create migration project: "WAVE1_GL_ACCOUNTS"
4. Upload GL account file (~1,000 records)
5. Map source fields to target template fields
6. Validate mandatory fields (account number, text, group, chart of accounts)
7. Simulate migration (review errors)
8. Correct data and re-upload if needed
9. Execute final migration in batches (200-300 accounts per batch)
10. Monitor execution log for errors

*File Format:* Migration Cockpit template format (CSV/Excel):
- Chart of Accounts, GL Account Number, Short Text, Long Text, Account Group, Balance Sheet Indicator, Company Code, Currency

*Key Configuration Parameters:*
- Batch size: 200-300 records per batch
- Company code: Load chart of accounts level first, then company code specific data
- Error tolerance: 0% for critical fields

**Pre-Import Validation:**

- [ ] No duplicate GL account numbers in source file
- [ ] All GL accounts have descriptions (TXT50 populated)
- [ ] Account groups (KTOKS) are valid
- [ ] Balance sheet/P&L indicator set correctly
- [ ] Reconciliation account flags appropriate for vendor/customer/asset accounts
- [ ] Cost element indicators match CO requirements
- [ ] Inactive/blocked accounts removed or flagged
- [ ] Account descriptions within 50 character limit
- [ ] Company code assignments complete for all 7 entities

**Post-Import Validation:**

- [ ] Record count: Source (~1,000) = Target (~1,000)
- [ ] All GL accounts have descriptions in S/4HANA
- [ ] Reconciliation account assignments correct (check sample: 110000, 120000, 210000, 220000)
- [ ] Can display GL account via FS00 in S/4HANA
- [ ] Cost element auto-creation completed (primary cost elements via KA03)
- [ ] No critical errors in migration log
- [ ] Test posting: Create sample document (FB50) to verify account accepts postings
- [ ] GL accounts available for cost center/profit center assignment

---

#### Object 4: Bank Master Data

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: FI12 (Bank Master Data Display)
- Tables: BNKA (Bank Master), T012 (House Banks), T012K (House Bank Accounts)
- Extract Fields: BANKS (Bank Key), BANKL (Bank Number), BANKA (Bank Name), SWIFT, STRAS (Street)
- Expected Records: ~50 banks

*Data Quality Checks:*
- [ ] Bank keys valid per country
- [ ] SWIFT codes formatted correctly (if international)
- [ ] Bank names complete
- [ ] No duplicate bank keys within country
- [ ] Address information complete

*Cleansing Rules:*
- Standardize bank names
- Validate SWIFT/BIC codes
- Complete missing address fields
- Remove inactive banks

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BANKS | Bank Country | Direct |
| BANKL | Bank Key | Direct |
| BANKA | Bank Name | Direct |
| SWIFT | SWIFT Code | Direct |

**Load Execution:**

*Migration Tool:* Migration Cockpit - FI_BANK template

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: FI_BANK
3. Create migration project: "WAVE1_BANK_MASTER"
4. Upload bank master file (~50 records)
5. Validate country and bank key combinations
6. Simulate migration
7. Execute final migration
8. Configure house banks separately (transaction FI12)

*File Format:* CSV/Excel:
- Country, Bank Key, Bank Name, SWIFT Code, Street, City, Region

*Key Configuration Parameters:*
- Load external banks first
- House banks may require manual configuration
- Bank account setup separate step

**Pre-Import Validation:**

- [ ] Bank keys valid per country
- [ ] SWIFT codes formatted correctly (if international)
- [ ] Bank names complete
- [ ] No duplicate bank keys within country
- [ ] Address information complete
- [ ] Inactive banks removed from source file

**Post-Import Validation:**

- [ ] Record count: Source (~50) = Target (~50)
- [ ] Sample bank lookups successful (transaction FI03)
- [ ] SWIFT codes validated and display correctly
- [ ] House banks configured with accounts
- [ ] Can be used in payment processing configuration
- [ ] Bank master data accessible for vendor/customer assignment

---

#### Object 5: Tax Codes

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: FTXP (Tax Code Display)
- Tables: T007A (Tax Codes), T007S (Tax Code Texts)
- Extract Fields: MWSKZ (Tax Code), TEXT1 (Description), KALSM (Tax Procedure), tax rates
- Expected Records: ~40 tax codes across 7 countries

*Data Quality Checks:*
- [ ] Tax codes unique per country/company code
- [ ] Tax rates accurate and current
- [ ] Descriptions clear and complete
- [ ] Tax procedure assignments correct
- [ ] GL account assignments for tax posting exist

*Cleansing Rules:*
- Verify tax rates with Finance team
- Update outdated rates to current rates (confirm cut-off date)
- Ensure tax type correctly categorized (input/output/VAT/GST)
- Map to S/4HANA tax procedure

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| MWSKZ | Tax Code | Direct |
| TEXT1 | Description | Direct |
| KALSM | Tax Procedure | Map to S/4 procedure |
| Tax Rate % | Tax Rate | Direct |

**Load Execution:**

*Migration Tool:* Manual Configuration (SPRO)

*Load Steps:*
1. Transaction: SPRO
2. Navigate: Financial Accounting > Financial Accounting Global Settings > Tax on Sales/Purchases > Calculation > Define Tax Codes
3. Create each tax code manually with correct rates
4. Assign GL accounts for tax posting (per company code)
5. Set jurisdiction codes (if applicable for US)
6. Test tax calculation

*Key Configuration Parameters:*
- Tax procedure: TAXUSJ (US), TAXCN (China), TAXSG (Singapore), etc.
- Posting logic: Automatic tax account determination
- Jurisdiction: Set for US10 company code

**Pre-Import Validation:**

- [ ] Tax codes unique per country/company code
- [ ] Tax rates accurate and current (verified with Finance team)
- [ ] Descriptions clear and complete
- [ ] Tax procedure assignments correct
- [ ] GL account assignments for tax posting exist
- [ ] Tax rates updated to current rates (confirm cut-off date)
- [ ] Tax type correctly categorized (input/output/VAT/GST)

**Post-Import Validation:**

- [ ] All ~40 tax codes created in S/4HANA
- [ ] Tax rates verified by Finance team post-load
- [ ] GL account determination configured and working
- [ ] Test transaction with tax code: Create invoice (FB60) with tax
- [ ] Tax calculation accurate (compare with expected results)
- [ ] Tax reports accessible (J1I3, FTAXP)
- [ ] Jurisdiction codes set correctly (if applicable for US)

---

#### Object 6: Payment Terms

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: OBB8 (Payment Terms Display)
- Table: T052 (Payment Terms)
- Extract Fields: ZTERM (Payment Term Key), TEXT1 (Description), days, discount %
- Expected Records: TBD (typically 10-20 terms)

*Data Quality Checks:*
- [ ] Payment term keys unique
- [ ] Descriptions complete
- [ ] Discount percentages and days logical
- [ ] Baseline date calculation rules defined

*Cleansing Rules:*
- Standardize payment term naming conventions
- Verify discount terms with AP/AR teams
- Remove obsolete terms

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| ZTERM | Payment Terms | Direct |
| TEXT1 | Description | Direct |
| Discount % | Discount Percentage | Direct |
| Days | Payment Days | Direct |

**Load Execution:**

*Migration Tool:* Manual Configuration (SPRO)

*Load Steps:*
1. Transaction: OBB8 or SPRO path
2. Navigate: Financial Accounting > Accounts Receivable/Accounts Payable > Business Transactions > Incoming Invoices/Credit Memos > Maintain Terms of Payment
3. Create each payment term with:
   - Payment term key
   - Description
   - Day limits
   - Discount percentages
   - Baseline date rules
4. Save configuration

**Pre-Import Validation:**

- [ ] Payment term keys unique
- [ ] Descriptions complete
- [ ] Discount percentages and days logical
- [ ] Baseline date calculation rules defined
- [ ] Standardized payment term naming conventions
- [ ] Discount terms verified with AP/AR teams
- [ ] Obsolete terms removed from source

**Post-Import Validation:**

- [ ] All payment terms created in S/4HANA
- [ ] Discount calculation logic verified (manual calculation check)
- [ ] Can be assigned to vendor/customer master (test assignment)
- [ ] Test in invoice entry (FB60/FB70)
- [ ] Due date calculation accurate (compare multiple scenarios)
- [ ] Payment terms available in drop-down lists

---

### 1.3 CO Foundation

#### Object 7: Cost Center Master

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: KS03 (Cost Center Display)
- Tables: CSKS (Cost Center Master), CSKT (Cost Center Texts)
- Extract Fields: KOSTL (Cost Center), KTEXT (Description), DATBI/DATAB (Validity), VERAK (Person Responsible)
- Expected Records: TBD (estimate based on org size)

*Data Quality Checks:*
- [ ] Cost center numbers unique
- [ ] Descriptions complete and meaningful
- [ ] Validity dates appropriate (standard: 01/01/YYYY - 12/31/9999)
- [ ] Person responsible fields populated
- [ ] Profit center assignments ready (dependency)
- [ ] Cost center category defined

*Cleansing Rules:*
- Remove inactive cost centers (or set end date)
- Standardize naming conventions
- Validate responsible person exists in HR
- Ensure controlling area assignment
- Map to correct cost center category

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| KOSTL | Cost Center | Direct |
| KTEXT | Description | Direct |
| DATAB | Valid From | Direct |
| DATBI | Valid To | Direct |
| VERAK | Person Responsible | Direct |
| PRCTR | Profit Center | Direct (from mapping) |

**Load Execution:**

*Migration Tool:* Migration Cockpit - CO_COST_CENTER template

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: CO_COST_CENTER
3. Create migration project: "WAVE1_COST_CENTERS"
4. Upload cost center file
5. Ensure controlling area = HC01 (or your area)
6. Map profit center assignments (mandatory in S/4HANA)
7. Validate cost center categories
8. Simulate migration
9. Execute final migration

*File Format:* CSV/Excel:
- Controlling Area, Cost Center, Description, Valid From, Valid To, Person Responsible, Profit Center, Cost Center Category, Company Code

*Key Configuration Parameters:*
- Controlling area: HC01
- Profit center: Mandatory assignment
- Validity: Use date range covering current and future periods

**Pre-Import Validation:**

- [ ] Cost center numbers unique
- [ ] Descriptions complete and meaningful
- [ ] Validity dates appropriate (standard: 01/01/YYYY - 12/31/9999)
- [ ] Person responsible fields populated
- [ ] Profit center assignments mapped and valid
- [ ] Cost center category defined
- [ ] Inactive cost centers removed or end-dated
- [ ] Naming conventions standardized
- [ ] Controlling area assignment = HC01

**Post-Import Validation:**

- [ ] Record count: Source = Target
- [ ] All cost centers assigned to profit centers (100%)
- [ ] Can display cost center via KS03
- [ ] Cost center accepts cost element postings (test via FB50)
- [ ] Person responsible field populated in S/4HANA
- [ ] Hierarchy assignment ready (Object 8)
- [ ] Test posting: Post to cost center via FB50 with GL account
- [ ] Cost centers available for asset master assignment

---

#### Object 8: Cost Center Hierarchy

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: OKEON (Standard Hierarchy Display)
- Tables: SETNODE, SETHEADER, SETLEAF
- Extract Fields: SETNAME (HC01), hierarchy structure nodes and assignments
- Expected Records: 1 hierarchy structure

*Data Quality Checks:*
- [ ] Hierarchy name = HC01
- [ ] All cost centers assigned to hierarchy
- [ ] Hierarchy structure logical (top-down organization)
- [ ] No orphan cost centers
- [ ] Node descriptions complete

*Cleansing Rules:*
- Verify organizational structure with stakeholders
- Ensure all active cost centers included
- Remove references to deleted cost centers
- Validate hierarchy levels appropriate

*Field Mapping:*
- Hierarchical structure with parent-child relationships

**Load Execution:**

*Migration Tool:* Manual Upload or Excel Template

*Load Steps:*
1. Transaction: OKEON (Maintain Cost Center Standard Hierarchy)
2. Create standard hierarchy: HC01
3. Build hierarchy structure:
   - Top node: Home Control (or company name)
   - Sub-nodes by function/department
   - Assign cost centers to appropriate nodes
4. Alternative: Use Excel upload tool if available
5. Save hierarchy
6. Activate hierarchy

*Key Configuration Parameters:*
- Hierarchy name: HC01
- Controlling area: HC01
- Standard hierarchy flag: Set

**Pre-Import Validation:**

- [ ] Hierarchy name = HC01
- [ ] All cost centers included in hierarchy structure
- [ ] Hierarchy structure logical (top-down organization)
- [ ] No orphan cost centers
- [ ] Node descriptions complete
- [ ] Organizational structure verified with stakeholders
- [ ] No references to deleted cost centers

**Post-Import Validation:**

- [ ] Hierarchy HC01 created in S/4HANA
- [ ] All cost centers assigned to hierarchy (100%)
- [ ] Hierarchy displays correctly in KSH1
- [ ] Can be used in reporting (S_ALR_87013611)
- [ ] No unassigned cost centers remain
- [ ] Hierarchy structure matches organizational design
- [ ] Standard hierarchy flag is set

---

#### Object 9: Profit Center Master

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: KE53 (Profit Center Display)
- Tables: CEPC (Profit Center Master), CEPCT (Profit Center Texts)
- Extract Fields: PRCTR (Profit Center), KTEXT (Description), DATBI/DATAB (Validity), VERAK (Person Responsible)
- Expected Records: TBD

*Data Quality Checks:*
- [ ] Profit center numbers unique
- [ ] Descriptions complete
- [ ] Validity dates appropriate
- [ ] Segment assignments ready (if using)
- [ ] Person responsible populated
- [ ] Profit center area = HC01

*Cleansing Rules:*
- Remove inactive profit centers
- Standardize naming
- Validate segment assignments
- Ensure controlling area alignment

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| PRCTR | Profit Center | Direct |
| KTEXT | Description | Direct |
| DATAB | Valid From | Direct |
| DATBI | Valid To | Direct |
| VERAK | Person Responsible | Direct |
| SEGMENT | Segment | Direct (if applicable) |

**Load Execution:**

*Migration Tool:* Migration Cockpit - CO_PROFIT_CENTER template

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: CO_PROFIT_CENTER
3. Create migration project: "WAVE1_PROFIT_CENTERS"
4. Upload profit center file
5. Ensure controlling area = HC01
6. Map segment assignments (if using segmentation)
7. Simulate migration
8. Execute final migration

*File Format:* CSV/Excel:
- Controlling Area, Profit Center, Description, Valid From, Valid To, Person Responsible, Segment, Company Code

*Key Configuration Parameters:*
- Controlling area: HC01
- Segment: Map if using segment reporting
- Validity: Full date range

**Pre-Import Validation:**

- [ ] Profit center numbers unique
- [ ] Descriptions complete
- [ ] Validity dates appropriate
- [ ] Segment assignments ready (if using)
- [ ] Person responsible populated
- [ ] Profit center area = HC01
- [ ] Inactive profit centers removed
- [ ] Naming conventions standardized
- [ ] Controlling area alignment verified

**Post-Import Validation:**

- [ ] Record count: Source = Target
- [ ] Can display profit center via KE53
- [ ] Profit centers available for cost center assignment
- [ ] Segment assignments correct (if applicable)
- [ ] Person responsible populated in S/4HANA
- [ ] Hierarchy assignment ready (Object 10)
- [ ] Profit centers available in drop-down selections

---

#### Object 10: Profit Center Hierarchy

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: KCH1 (Standard Hierarchy Display)
- Tables: SETNODE, SETHEADER, SETLEAF
- Extract Fields: Hierarchy structure HC01
- Expected Records: 1 hierarchy structure

*Data Quality Checks:*
- [ ] Hierarchy name = HC01
- [ ] All profit centers assigned
- [ ] Structure aligns with business segments
- [ ] No orphan profit centers

*Cleansing Rules:*
- Validate structure with management
- Ensure alignment with cost center hierarchy
- Complete node descriptions

**Load Execution:**

*Migration Tool:* Manual Configuration or Excel Upload

*Load Steps:*
1. Transaction: KCH1 (Maintain Profit Center Standard Hierarchy)
2. Create standard hierarchy: HC01
3. Build structure with nodes and assignments
4. Assign all profit centers
5. Save and activate

**Pre-Import Validation:**

- [ ] Hierarchy name = HC01
- [ ] All profit centers assigned in hierarchy structure
- [ ] Structure aligns with business segments
- [ ] No orphan profit centers
- [ ] Node descriptions complete
- [ ] Structure validated with management
- [ ] Alignment with cost center hierarchy confirmed

**Post-Import Validation:**

- [ ] Hierarchy HC01 created in S/4HANA
- [ ] All profit centers assigned (100%)
- [ ] Displays correctly in KCH2
- [ ] Available for reporting
- [ ] Standard hierarchy flag is set
- [ ] Hierarchy structure matches business design

---

#### Object 11: Primary Cost Elements

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: KA03 (Cost Element Display)
- Table: CSKU (Cost Elements)
- Extract Fields: Cost element = GL account for primary
- Expected Records: Auto-created from GL accounts

*Data Quality Checks:*
- [ ] All P&L GL accounts flagged as primary cost elements
- [ ] Cost element categories assigned correctly
- [ ] Default cost center assignments (if any)

*Cleansing Rules:*
- Verify cost element categories
- Set default cost centers where appropriate
- Enable/disable cost element flags as needed

**Load Execution:**

*Migration Tool:* System Automatic (from GL Account Master)

*Load Steps:*
1. Primary cost elements auto-create when GL accounts are created with cost element flag
2. Verify auto-creation via KA03
3. Update cost element categories if needed (transaction KA02)
4. Set default account assignments if required

*Key Configuration Parameters:*
- Automatic creation triggered by GL account cost element indicator
- Cost element category: 01 (primary cost element/revenue)

**Pre-Import Validation:**

- [ ] All P&L GL accounts flagged as primary cost elements
- [ ] Cost element categories assigned correctly in GL master
- [ ] Default cost center assignments identified (if any)
- [ ] GL accounts with cost element indicator verified

**Post-Import Validation:**

- [ ] All expense/revenue GL accounts have corresponding cost elements (via KA03)
- [ ] Cost element categories correct (category 01)
- [ ] Can post to cost elements with cost center (test via FB50)
- [ ] Cost elements visible in CO reporting
- [ ] Auto-creation from GL accounts successful
- [ ] No missing primary cost elements

---

#### Object 12: Secondary Cost Elements

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: KA03 (Cost Element Display)
- Table: CSKU
- Extract Fields: Secondary cost elements (no GL account)
- Expected Records: TBD (assessment, distribution, internal orders)

*Data Quality Checks:*
- [ ] Secondary cost element numbers unique
- [ ] Descriptions complete
- [ ] Cost element categories appropriate (21, 22, 31, 41, 42, 43)
- [ ] No overlap with GL account numbers

*Cleansing Rules:*
- Standardize number ranges for secondary elements
- Verify categories match usage
- Remove obsolete elements

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| KSTAR | Cost Element | Direct |
| KTEXT | Description | Direct |
| KOART | Cost Element Category | Direct |

**Load Execution:**

*Migration Tool:* Manual Creation (transaction KA01)

*Load Steps:*
1. Transaction: KA01 (Create Cost Element)
2. For each secondary cost element:
   - Enter cost element number
   - Select cost element category (21=Assessment, 22=Distrib, 31=Int Order, etc.)
   - Enter description
   - Set validity dates
   - Save
3. Repeat for all secondary cost elements

*Key Configuration Parameters:*
- Controlling area: HC01
- Category must match usage (allocations, internal orders, etc.)

**Pre-Import Validation:**

- [ ] Secondary cost element numbers unique
- [ ] Descriptions complete
- [ ] Cost element categories appropriate (21, 22, 31, 41, 42, 43)
- [ ] No overlap with GL account numbers
- [ ] Number ranges for secondary elements standardized
- [ ] Categories match intended usage
- [ ] Obsolete elements removed

**Post-Import Validation:**

- [ ] All secondary cost elements created in S/4HANA
- [ ] Categories appropriate for planned usage (verified via KA03)
- [ ] Can be used in allocation cycles (test in KSU1)
- [ ] Available for internal order settlement
- [ ] Record count: Source = Target
- [ ] Cost elements display correctly via KA03

---

#### Object 13: Statistical Key Figures

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: KK03 (Statistical Key Figure Display)
- Table: TKA02
- Extract Fields: Key figure number, text, unit of measure
- Expected Records: TBD (e.g., headcount, square footage, machine hours)

*Data Quality Checks:*
- [ ] Key figure numbers unique
- [ ] Descriptions clear
- [ ] Units of measure defined
- [ ] Fixed/total value categories set

*Cleansing Rules:*
- Verify with management which KFs still needed
- Remove obsolete key figures
- Standardize naming

**Load Execution:**

*Migration Tool:* Manual Creation (transaction KK01)

*Load Steps:*
1. Transaction: KK01 (Create Statistical Key Figure)
2. For each key figure:
   - Enter key figure number
   - Enter description
   - Select unit of measure
   - Set fixed/total value indicator
   - Set validity dates
   - Save
3. Repeat for all key figures

**Pre-Import Validation:**

- [ ] Key figure numbers unique
- [ ] Descriptions clear
- [ ] Units of measure defined
- [ ] Fixed/total value categories set
- [ ] Verified with management which KFs still needed
- [ ] Obsolete key figures removed
- [ ] Naming conventions standardized

**Post-Import Validation:**

- [ ] All key figures created in S/4HANA (via KK03)
- [ ] Can post key figure values via KB31N (test posting)
- [ ] Available for allocation base in KSU1
- [ ] Reporting accessible
- [ ] Record count: Source = Target
- [ ] Units of measure display correctly

---

### 1.4 Asset Accounting

#### Object 14: Fixed Asset Master

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: AS03 (Asset Display)
- Tables: ANLA (Asset Master), ANLB (Depreciation), ANLC (Asset Values), ANLZ (Time-Dependent)
- Extract Fields: ANLN1 (Asset Number), TXT50 (Description), asset class, cost center, depreciation keys, acquisition values
- Expected Records: TBD

*Data Quality Checks:*
- [ ] Asset numbers unique
- [ ] Descriptions complete
- [ ] Asset classes valid
- [ ] Cost center assignments exist and valid
- [ ] Depreciation areas configured (01, 15, etc.)
- [ ] GL account determination complete
- [ ] Capitalization dates accurate

*Cleansing Rules:*
- Remove fully depreciated and retired assets (or flag for historical)
- Validate cost center assignments against new cost center list
- Ensure asset classes mapped to S/4HANA asset classes
- Complete missing mandatory fields
- Reconcile asset values to GL

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| ANLN1 | Asset Number | Direct |
| TXT50 | Asset Description | Direct |
| ANLKL | Asset Class | Map to S/4 classes |
| KOSTL | Cost Center | Map to new cost centers |
| ZUGDT | Capitalization Date | Direct |
| AFABE | Depreciation Area | Direct |

**Load Execution:**

*Migration Tool:* Migration Cockpit - FI_ASSET_MASTER template

*Load Steps:*
1. Prerequisite: Asset classes configured in SPRO
2. Transaction: LTMC
3. Select migration object: FI_ASSET_MASTER
4. Create migration project: "WAVE1_FIXED_ASSETS"
5. Upload asset master file (master data only, no balances)
6. Map asset classes
7. Validate cost center assignments
8. Simulate migration (expect high error rate first time)
9. Correct errors iteratively
10. Execute final migration in batches

*File Format:* Migration template with fields:
- Company Code, Asset Number, Asset Class, Description, Cost Center, Capitalization Date, Business Area, Depreciation Key, Useful Life

*Key Configuration Parameters:*
- Company code: All 7 company codes
- Depreciation areas: Must be pre-configured
- GL account determination: Asset class settings
- Number range: Internal or external assignment

**Pre-Import Validation:**

- [ ] Asset numbers unique
- [ ] Descriptions complete
- [ ] Asset classes valid and mapped to S/4HANA asset classes
- [ ] Cost center assignments exist and valid (verified against new cost center list)
- [ ] Depreciation areas configured (01, 15, etc.)
- [ ] GL account determination complete for asset classes
- [ ] Capitalization dates accurate
- [ ] Fully depreciated and retired assets removed or flagged
- [ ] All mandatory fields populated
- [ ] Asset values reconciled to GL in source system

**Post-Import Validation:**

- [ ] Record count: Source = Target
- [ ] Asset classes correctly assigned in S/4HANA
- [ ] Cost center assignments valid (all cost centers exist)
- [ ] GL account determination working (check via AS03)
- [ ] Sample asset can accept transactions (ABZON test)
- [ ] Depreciation keys assigned correctly
- [ ] Asset master displays correctly via AS03
- [ ] Asset values will be loaded in Wave 3 (balances)
- [ ] No critical errors in migration log

---

## Wave 1 Load Sequence

### Execution Order with Dependencies

**Phase 1: Organizational Foundation**  
*Duration: Day 1*

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 1.1 | Chart of Accounts | Manual (OB13) | 15 min | None | [ ] |
| 1.2 | Company Code Structure | LTMC | 1 hour | Chart of Accounts | [ ] |

**Phase 2: FI Foundation (Parallel Processing)**  
*Duration: Day 1-2*

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 2.1 | GL Account Master | LTMC - FI_GL_ACCOUNT | 4-6 hours | CoA, Company Codes | [ ] |
| 2.2 | Bank Master Data | LTMC - FI_BANK | 2 hours | None (parallel with 2.1) | [ ] |

**Phase 3: FI Configuration**  
*Duration: Day 2*

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 3.1 | Tax Codes | Manual (FTXP/SPRO) | 2-3 hours | GL Accounts | [ ] |
| 3.2 | Payment Terms | Manual (OBB8) | 1 hour | None (parallel with 3.1) | [ ] |

**Phase 4: CO Foundation (Parallel Processing)**  
*Duration: Day 2-3*

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 4.1 | Cost Center Master | LTMC - CO_COST_CENTER | 2-3 hours | GL Accounts | [ ] |
| 4.2 | Profit Center Master | LTMC - CO_PROFIT_CENTER | 2-3 hours | None (parallel with 4.1) | [ ] |

**Phase 5: CO Hierarchies**  
*Duration: Day 3*

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 5.1 | Cost Center Hierarchy | Manual (OKEON) | 1-2 hours | Cost Centers | [ ] |
| 5.2 | Profit Center Hierarchy | Manual (KCH1) | 1-2 hours | Profit Centers | [ ] |

**Phase 6: CO Elements**  
*Duration: Day 3*

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 6.1 | Primary Cost Elements | Automatic | 30 min | GL Accounts (auto) | [ ] |
| 6.2 | Secondary Cost Elements | Manual (KA01) | 1-2 hours | Primary Cost Elements | [ ] |
| 6.3 | Statistical Key Figures | Manual (KK01) | 1 hour | None (parallel with 6.2) | [ ] |

**Phase 7: Asset Accounting**  
*Duration: Day 4-5*

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 7.1 | Fixed Asset Master | LTMC - FI_ASSET_MASTER | 6-8 hours | GL Accounts, Cost Centers, Asset Classes | [ ] |

### Total Estimated Duration: 3-5 Days

**Critical Path:**  
Chart of Accounts → Company Codes → GL Accounts → Cost Centers → Fixed Assets

**Parallel Processing Opportunities:**
- Day 1-2: GL Accounts + Bank Master
- Day 2: Tax Codes + Payment Terms
- Day 2-3: Cost Centers + Profit Centers
- Day 3: Cost Center Hierarchy + Profit Center Hierarchy
- Day 3: Secondary Cost Elements + Statistical Key Figures

---

## Validation & Sign-Off Checklist

### Wave 1 Completion Criteria

**Organizational Structure Validation**

- [ ] Chart of Accounts YCOA created and active
- [ ] All 7 company codes created (SG21, CN13, CN17, US10, BE10, HCIL, BR10)
- [ ] Company codes assigned to Chart of Accounts YCOA
- [ ] Company codes have correct currencies
- [ ] Fiscal year variant K4 assigned to all company codes

**FI Foundation Validation**

- [ ] ~1,000 GL accounts loaded successfully
- [ ] Record count: ECC source = S/4HANA target
- [ ] All GL accounts have descriptions
- [ ] GL account groups correctly assigned
- [ ] Reconciliation account indicators set correctly (vendor, customer, asset accounts)
- [ ] Sample GL accounts display correctly (FS00)
- [ ] Test posting to sample GL account successful (FB50)
- [ ] Bank master data loaded (~50 banks)
- [ ] House banks configured with accounts
- [ ] Tax codes created (~40 codes)
- [ ] Tax rate calculations tested and accurate
- [ ] Payment terms created (all terms)
- [ ] Payment term discount calculation verified

**CO Foundation Validation**

- [ ] All cost centers loaded
- [ ] All profit centers loaded
- [ ] Cost centers assigned to profit centers (100%)
- [ ] Cost center hierarchy HC01 created
- [ ] All cost centers assigned to hierarchy
- [ ] Profit center hierarchy HC01 created
- [ ] All profit centers assigned to hierarchy
- [ ] Primary cost elements created (auto from GL)
- [ ] Secondary cost elements created (manual)
- [ ] Statistical key figures created
- [ ] Test posting to cost center successful (FB50 with cost center)

**Asset Accounting Validation**

- [ ] Fixed asset master loaded
- [ ] Record count reconciliation (source = target)
- [ ] Asset classes correctly assigned
- [ ] Cost center assignments valid
- [ ] GL account determination working
- [ ] Depreciation keys assigned
- [ ] Sample asset displays correctly (AS03)
- [ ] Asset ready for balance load in Wave 3

**Data Quality Validation**

- [ ] No duplicate records in any master data object
- [ ] All mandatory fields populated
- [ ] No critical errors in migration logs
- [ ] Error rate < 2% (and all errors resolved)
- [ ] All validation reports executed and passed

**Integration Validation**

- [ ] GL accounts can be used by FI transactions
- [ ] Cost centers can be used in CO postings
- [ ] Asset master references valid GL accounts and cost centers
- [ ] Bank master ready for payment processing
- [ ] Tax codes ready for invoice entry

**Technical Validation**

- [ ] All Migration Cockpit projects completed
- [ ] All manual configurations saved
- [ ] Configuration transport created (if applicable)
- [ ] Migration logs archived
- [ ] Source files backed up

### Sign-Off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| FI Lead | | | |
| CO Lead | | | |
| Data Migration Lead | | | |
| Project Manager | | | |

**Wave 1 Status:** [ ] Complete [ ] Incomplete

**Ready to Proceed to Wave 2:** [ ] Yes [ ] No

**If No, Outstanding Items:**
1. 
2. 
3. 

---

## Troubleshooting Quick Reference

### Common Issues and Resolutions

#### GL Account Master Issues

**Issue:** GL accounts fail to load with error "Chart of Accounts does not exist"
- **Cause:** Chart of Accounts not created or incorrect CoA in file
- **Resolution:** Verify YCOA exists via OB13, correct CoA field in upload file

**Issue:** GL accounts loaded but cannot post
- **Cause:** Posting block set or account group restrictions
- **Resolution:** Check field status group in account group (OBD4), remove posting blocks via FS00

**Issue:** Cost element not auto-created for P&L accounts
- **Cause:** Cost element indicator not set in GL account
- **Resolution:** Edit GL account (FS00), set cost element category in controlling area data

**Issue:** Balance check fails showing non-zero balance
- **Cause:** Wave 1 loads master data only, no balances expected
- **Resolution:** Confirm this is expected, balances load in Wave 3

#### Cost Center Issues

**Issue:** Cost centers fail to load with error "Profit center does not exist"
- **Cause:** Profit center assignment invalid or profit center not loaded
- **Resolution:** Load profit centers first, verify profit center numbers in cost center file

**Issue:** Cost center assignment errors in posting test
- **Cause:** Cost center not valid on posting date
- **Resolution:** Check validity dates (KS03), extend validity if needed via KS02

**Issue:** Cost center hierarchy assignment missing
- **Cause:** Standard hierarchy not maintained or cost center not assigned
- **Resolution:** Maintain hierarchy via OKEON, assign all cost centers

#### Asset Master Issues

**Issue:** High error rate in asset master load (>20%)
- **Cause:** Common on first load - cost center, asset class, depreciation key issues
- **Resolution:** Iterative approach - fix errors in batches, reload

**Issue:** Asset class does not exist
- **Cause:** Asset class not configured in S/4HANA
- **Resolution:** Configure asset classes in SPRO before loading assets

**Issue:** Cost center assignment invalid
- **Cause:** Cost center doesn't exist or not valid for company code
- **Resolution:** Validate cost center mapping, ensure cost centers loaded in Step 4.1

**Issue:** GL account determination missing
- **Cause:** Asset class GL account assignment incomplete
- **Resolution:** Complete GL account determination for asset class (transaction OAYZ)

#### Migration Cockpit Issues

**Issue:** Migration Cockpit template not found
- **Cause:** Template not activated or not available in cloud version
- **Resolution:** Activate via LTMOM, or use custom migration object

**Issue:** File upload fails with format error
- **Cause:** File format doesn't match template
- **Resolution:** Download template from LTMC, match column headers exactly

**Issue:** Simulation successful but execution fails
- **Cause:** Data changed between simulation and execution, or locking issues
- **Resolution:** Re-run simulation, check for locks (SM12), execute immediately after simulation

#### Configuration Issues

**Issue:** Company code cannot be assigned to controlling area
- **Cause:** Controlling area not created or configuration incomplete
- **Resolution:** Create controlling area HC01 via transaction OKKP before loading CO objects

**Issue:** Tax code calculation incorrect
- **Cause:** Tax procedure not assigned or tax percentage wrong
- **Resolution:** Verify tax procedure assignment (OBCL), check tax percentage in FTXP

**Issue:** Payment terms not available in vendor master
- **Cause:** Payment terms not created or maintained incorrectly
- **Resolution:** Verify via OBB8, check language and baseline date settings

### Escalation Path

**Level 1:** Data Migration Team Member
- Resolve common errors using this troubleshooting guide
- Correct data and retry

**Level 2:** Functional Lead (FI/CO)
- Complex functional issues
- Configuration questions
- Business rule clarifications

**Level 3:** Technical Lead / SAP Basis
- System issues
- Performance problems
- Authorization issues

**Level 4:** Project Manager
- Timeline impact
- Resource needs
- Go/No-Go decisions

### Key Contacts

| Role | Name | Email | Phone |
|------|------|-------|-------|
| FI Lead | Frey Zheng | | |
| CO Lead | | | |
| MM Lead | Meos Xu | | |
| Data Migration Lead | | | |
| Project Manager | | | |

### Useful Transaction Codes

**Display Transactions:**
- FS00 - GL Account Display
- KS03 - Cost Center Display
- KE53 - Profit Center Display
- AS03 - Asset Display
- FI03 - Bank Display
- FTXP - Tax Code Display

**Maintenance Transactions:**
- FS02 - GL Account Change
- KS02 - Cost Center Change
- KE52 - Profit Center Change
- AS02 - Asset Change

**Migration Tools:**
- LTMC - Migration Cockpit
- LTMOM - Migration Object Modeler

**Validation Reports:**
- S_ALR_87012357 - GL Account List
- S_ALR_87013611 - Cost Center List
- S_ALR_87012993 - Asset List

---

**End of Wave 1 Execution Runbook**

**Next Steps:**
- Upon completion of Wave 1 validation and sign-off
- Proceed to Wave 2: Business Partner & Material Master
- Estimated start: T-3 weeks before Go-Live

