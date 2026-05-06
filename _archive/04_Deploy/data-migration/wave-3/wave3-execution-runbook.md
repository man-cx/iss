# Wave 3: Transactional Data & Open Items - Execution Runbook
**SAP ECC to S/4HANA Cloud - Home Control**

**Document Version:** 1.0  
**Wave:** 3 - Transactional Data & Open Items  
**Date:** November 2025  
**Timing:** T-1 week (Mock Cutover) and Go-Live Weekend  
**Duration:** Mock (2 days) + Final (8-12 hours)  
**Objects Covered:** 12 transactional objects

---

## Table of Contents

1. [Pre-Migration Activities](#pre-migration-activities)
2. [Execution Procedures by Object](#execution-procedures-by-object)
   - [3.1 Financial Balances & Open Items](#31-financial-balances--open-items)
     - [Object 25: GL Account Balances](#object-25-gl-account-balances)
     - [Object 26: GL Open Line Items](#object-26-gl-open-line-items)
     - [Object 27: AP Open Items](#object-27-ap-open-items)
     - [Object 28: AR Open Items](#object-28-ar-open-items)
     - [Object 29: Fixed Asset Balances](#object-29-fixed-asset-balances)
   - [3.2 Inventory & Stock](#32-inventory--stock)
     - [Object 30: Inventory Stock Balances](#object-30-inventory-stock-balances)
     - [Object 31: Stock at Subcontractor](#object-31-stock-at-subcontractor)
     - [Object 32: Physical Inventory Counts](#object-32-physical-inventory-counts)
   - [3.3 Open Procurement Documents](#33-open-procurement-documents)
     - [Object 33: Open Purchase Orders](#object-33-open-purchase-orders)
     - [Object 34: Open Purchase Requisitions](#object-34-open-purchase-requisitions)
   - [3.4 Open Sales Documents](#34-open-sales-documents)
     - [Object 35: Open Sales Orders](#object-35-open-sales-orders)
     - [Object 36: Sales Contracts](#object-36-sales-contracts)
3. [Wave 3 Load Sequence](#wave-3-load-sequence)
4. [Validation & Sign-Off Checklist](#validation--sign-off-checklist)
5. [Troubleshooting Quick Reference](#troubleshooting-quick-reference)

---

## Pre-Migration Activities

### System Readiness Checks

**S/4HANA Environment:**
- [ ] Production system available and locked for migration
- [ ] Final system configuration complete
- [ ] All Wave 1 and Wave 2 objects validated
- [ ] Sufficient storage for transaction data
- [ ] System performance optimized
- [ ] Database backup completed before Wave 3 start

**ECC Source System:**
- [ ] Data freeze notification sent to all users
- [ ] Source system accessible for final extraction
- [ ] ECC backup completed at cutoff time
- [ ] Read-only access configured (for final cutover)

### User Access Verification

**Required Authorizations:**
- [ ] Migration Cockpit access (LTMC)
- [ ] Financial transaction posting authorizations (FB01, FB50)
- [ ] Material document posting authorizations (MIGO)
- [ ] All company codes accessible
- [ ] Display and reporting authorizations for validation

**Team Access:**
- [ ] FI Lead has full posting authorization
- [ ] MM Lead has goods movement authorization
- [ ] SD Lead has sales document authorization
- [ ] Technical migration lead has system administration access

### Template Downloads and Preparation

**Migration Cockpit Templates:**
- [ ] Download FI_BALANCE template (GL Balances)
- [ ] Download FI_GL_OPEN_ITEMS template
- [ ] Download FI_AP_OPEN_ITEMS template
- [ ] Download FI_AR_OPEN_ITEMS template
- [ ] Download FI_ASSET_TRANSACTIONS template
- [ ] Download MM_STOCK template
- [ ] Download MM_SUBCON_STOCK template
- [ ] Download MM_PURCHASE_ORDER template
- [ ] Download MM_PURCHASE_REQ template
- [ ] Download SD_SALES_ORDER template
- [ ] Download SD_CONTRACT template

**File Preparation:**
- [ ] Create working folder: `/wave3/source/`, `/wave3/staging/`, `/wave3/loaded/`
- [ ] Prepare reconciliation templates (Trial Balance, AP/AR Aging, Stock Value)
- [ ] Set up validation tracking spreadsheet

### Source Data Extraction from ECC

**Financial Data Extraction (Critical Timing):**
- [ ] Extract GL account balances as of cutoff date (last day of month)
- [ ] Extract GL open line items (table BSEG where AUGBL is blank)
- [ ] Extract AP open items (table BSIK - open items, BSAK - cleared for reference)
- [ ] Extract AR open items (table BSID - open items, BSAD - cleared for reference)
- [ ] Extract Fixed Asset balances (tables ANLA, ANLC)

**ECC Tables for Financial Data:**
- `BKPF` - Accounting Document Header
- `BSEG` - Accounting Document Segment (All postings)
- `BSIK` - AP Open Items
- `BSAK` - AP Cleared Items
- `BSID` - AR Open Items
- `BSAD` - AR Cleared Items
- `FAGLFLEXA` - GL Account Line Items
- `ANLA` - Asset Master Data
- `ANLC` - Asset Values

**Inventory Data Extraction:**
- [ ] Execute physical inventory count 48 hours before cutoff
- [ ] Freeze inventory movements during count
- [ ] Extract stock balances (table MARD - Storage Location Stock, MCHB - Batch Stock)
- [ ] Extract stock at subcontractor (table MSKU)
- [ ] Extract stock values from valuation (table MBEW)

**ECC Tables for Inventory:**
- `MARA` - Material Master General Data
- `MARD` - Material Storage Location Data
- `MCHB` - Material Batch Stock
- `MBEW` - Material Valuation
- `MSKU` - Subcontractor Stock

**Open Documents Extraction:**
- [ ] Extract open purchase orders (table EKKO, EKPO where delivery not complete)
- [ ] Extract open purchase requisitions (table EBAN where not deleted/closed)
- [ ] Extract open sales orders (table VBAK, VBAP where delivery status not complete)
- [ ] Extract sales contracts (table VBAK where contract not expired)

**ECC Tables for Open Documents:**
- `EKKO` - PO Header
- `EKPO` - PO Item
- `EBAN` - Purchase Requisition
- `VBAK` - Sales Document Header
- `VBAP` - Sales Document Item
- `VBUK` - Sales Document Header Status

### Data Cutoff Procedures

**Financial Data Cutoff (Critical):**
- [ ] Set cutoff date: Last day of month preceding Go-Live
- [ ] Communicate freeze period to Finance team (48 hours before cutover)
- [ ] Complete all month-end closing activities before cutoff
- [ ] Post all outstanding invoices through cutoff date
- [ ] Complete all clearing activities (payments, receipts) through cutoff
- [ ] Run final ECC reports at cutoff: Trial Balance, AP Aging, AR Aging
- [ ] Lock ECC posting periods after cutoff (or restrict to read-only)

**Inventory Cutoff:**
- [ ] Schedule physical inventory count 48 hours before cutover
- [ ] Freeze all inventory movements during count
- [ ] Complete cycle counting and reconcile variances
- [ ] Post all goods receipts and issues through cutoff date
- [ ] Run final stock value report in ECC
- [ ] Lock inventory transactions in ECC after count

**Open Documents Freeze:**
- [ ] Freeze creation of new purchase orders 24 hours before cutover
- [ ] Freeze creation of new sales orders 24 hours before cutover
- [ ] Complete in-flight transactions (GRs, invoices for existing POs/SOs)
- [ ] Communicate freeze to Purchasing and Sales teams

### Reconciliation Preparation

**Prepare Reconciliation Reports in ECC (Final Run):**
- [ ] Financial Accounting Trial Balance (all company codes)
- [ ] AP Aging Report (as of cutoff date)
- [ ] AR Aging Report (as of cutoff date)
- [ ] Stock Value Report (all plants, all materials)
- [ ] Fixed Asset Register (net book value by asset)
- [ ] Open PO Report (quantity and value)
- [ ] Open SO Report (quantity and value)
- [ ] Print and save all reports as baseline for S/4HANA comparison

---

## Execution Procedures by Object

## 3.1 Financial Balances & Open Items

### Object 25: GL Account Balances

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: FAGLB03 (GL Account Balances)
- Table: FAGLFLEXA (General Ledger: Actual Line Items)
- Extract Fields: Company Code, GL Account, Fiscal Year, Posting Period, Debit Amount, Credit Amount, Currency, Cost Center, Profit Center
- Expected Records: Balance for each GL account per company code
- Cutoff Date: Last day of month preceding Go-Live

*Data Quality Checks:*
- [ ] Trial balance totals: Debit = Credit for each company code
- [ ] Balance sheet accounts have correct debit/credit balance signs
- [ ] P&L accounts balance to zero (or carry year-to-date if mid-year)
- [ ] All company codes included (SG21, CN13, CN17, US10, BE10, HCIL, BR10)
- [ ] Cost center and profit center assignments present where required
- [ ] No balances on blocked or deleted GL accounts

*Cleansing Rules:*
- Consolidate balance at GL account level (summarize line items if needed)
- Validate currency matches company code local currency
- Ensure cost center/profit center assignments valid (cross-reference Wave 1)
- Zero-balance accounts can be excluded (optional)
- Aggregate by posting period if month-by-month load preferred

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BUKRS | Company Code | Direct |
| RACCT | GL Account | Direct |
| GJAHR | Fiscal Year | Direct |
| TSL | Amount in Local Currency | Direct |
| HSL | Amount in Group Currency | Direct |
| PRCTR | Profit Center | Direct |
| KOSTL | Cost Center | Direct (if balance sheet account) |
| SEGMENT | Segment | Map if using segment reporting |

*Balance Reconciliation Procedures:*
- [ ] Run Trial Balance in ECC for all company codes
- [ ] Export to Excel and calculate totals
- [ ] Debit total = Credit total (fundamental rule)
- [ ] Compare Balance Sheet total to prior period (reasonableness check)
- [ ] Review significant variances in account balances
- [ ] Obtain Finance sign-off on ECC balances before migration

**Load Execution:**

*Migration Tool:* ACDOCA Direct Posting or FI_BALANCE template

*Load Steps:*
1. Transaction: LTMC (Migration Cockpit) or FB50 (Journal Entry for initial balances)
2. Select migration object: FI_BALANCE or use opening balance posting
3. Create migration project: "WAVE3_GL_BALANCES"
4. Upload prepared balance file
5. Validate company code, fiscal year, posting period
6. Execute simulation
7. Review simulation log (check for balance errors)
8. Execute final load
9. Post balances to appropriate opening balance posting period

*File Format:* CSV or Excel with columns:
- Company Code, GL Account, Fiscal Year, Posting Period, Debit Amount, Credit Amount, Cost Center, Profit Center, Document Date, Posting Date, Document Text

*Key Configuration Parameters:*
- Posting period: Use special opening balance period (often period 00 or 13)
- Document type: AA (Asset Posting) or SA (GL Account Document)
- Posting key: 40 (Debit), 50 (Credit)
- Document date: Cutoff date (last day of month)
- Batch processing: Load by company code in separate batches

*Batch Processing Strategy:*
- Batch 1: Balance sheet accounts (assets, liabilities, equity)
- Batch 2: P&L accounts (if mid-year cutover)
- Separate batches per company code if large volume

**Pre-Import Validation:**

- [ ] Trial balance in source file: Debit = Credit
- [ ] All GL accounts exist in S/4HANA (loaded in Wave 1)
- [ ] Cost centers valid (loaded in Wave 1)
- [ ] Profit centers valid (loaded in Wave 1)
- [ ] Fiscal year and posting period valid in S/4HANA
- [ ] Currency codes match company code settings
- [ ] No balances on blocked accounts
- [ ] Balance signs correct (assets=debit, liabilities=credit)
- [ ] Total balance sheet agrees to ECC trial balance
- [ ] Opening balance posting period is open in S/4HANA

**Post-Import Validation:**

- [ ] Run Trial Balance in S/4HANA (transaction FAGLB03)
- [ ] Compare to ECC trial balance line-by-line
- [ ] Verify: S/4HANA Debit Total = ECC Debit Total
- [ ] Verify: S/4HANA Credit Total = ECC Credit Total
- [ ] Variance must be zero (no tolerance accepted)
- [ ] Check balance sheet total = ECC balance sheet total
- [ ] Verify cost center and profit center postings (report S_ALR_87013611)
- [ ] Sample GL accounts: Display line items (transaction FBL3N) to verify balances
- [ ] Check segment reporting balances (if applicable)
- [ ] Verify opening balance documents posted (transaction FB03)
- [ ] Functional testing: Post sample transaction (FB50) to ensure system accepts postings

---

### Object 26: GL Open Line Items

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: FBL3N (GL Account Line Item Display)
- Table: BSEG (where AUGBL is blank = open items)
- Extract Fields: Company Code, GL Account, Document Number, Fiscal Year, Line Item, Posting Date, Document Date, Amount, Currency, Assignment, Text, Cost Center, Profit Center
- Expected Records: Open items for GL accounts managed on open item basis
- Examples: GR/IR account, tax clearing accounts, suspense accounts

*Data Quality Checks:*
- [ ] Only accounts with open item management flag set
- [ ] Open items not cleared (AUGBL field blank)
- [ ] Document numbers valid
- [ ] Posting dates within valid range
- [ ] Amounts and currency correct
- [ ] Assignment field populated (for clearing)

*Cleansing Rules:*
- Review old open items (>90 days) for legitimacy
- Clear stale items in ECC before migration if possible
- Ensure assignment field populated to enable future clearing
- Validate special GL indicators if applicable

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BUKRS | Company Code | Direct |
| HKONT | GL Account | Direct |
| BELNR | Document Number | Direct |
| GJAHR | Fiscal Year | Direct |
| BUZEI | Line Item | Direct |
| BUDAT | Posting Date | Direct |
| BLDAT | Document Date | Direct |
| DMBTR | Amount in Local Currency | Direct |
| ZUONR | Assignment | Direct |
| SGTXT | Line Item Text | Direct |

**Load Execution:**

*Migration Tool:* FI_GL_OPEN_ITEMS template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: FI_GL_OPEN_ITEMS
3. Create migration project: "WAVE3_GL_OPEN_ITEMS"
4. Upload prepared file
5. Validate field mappings
6. Simulate migration
7. Execute final migration

*Key Configuration Parameters:*
- Post as separate documents or combined
- Retain original document numbers (if S/4HANA allows)
- Posting date: Original posting date or cutoff date
- Batch size: 500 line items per batch

**Pre-Import Validation:**

- [ ] All GL accounts exist and have open item management flag
- [ ] Document numbers unique
- [ ] Assignment field populated for clearing
- [ ] Amounts balanced (overall debit = credit for reconciliation)

**Post-Import Validation:**

- [ ] Count of open items: S/4HANA = ECC
- [ ] Total amount of open items reconciles
- [ ] Display sample line items (FBL3N) to verify details
- [ ] Test clearing functionality with sample open item (F-03)

---

### Object 27: AP Open Items

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: FBL1N (Vendor Line Item Display)
- Table: BSIK (Vendor Open Items)
- Extract Fields: Company Code, Vendor Number, Document Number, Fiscal Year, Line Item, Posting Date, Due Date, Amount, Currency, Payment Terms, Assignment
- Expected Records: All open vendor invoices and credit memos as of cutoff date
- **Critical:** This is balance-critical data - zero discrepancy tolerance

*Data Quality Checks:*
- [ ] All vendors exist in S/4HANA (loaded in Wave 2)
- [ ] Open item amounts match AP sub-ledger
- [ ] Due dates calculated correctly based on payment terms
- [ ] Aging buckets correct (current, 30 days, 60 days, 90+ days)
- [ ] No cleared items included (AUGBL blank)
- [ ] Partial payments accounted for correctly

*Cleansing Rules:*
- Review and clear old open items (>180 days) before migration if possible
- Confirm disputed items with vendors
- Clear small-value items (e.g., <$1) in ECC before migration
- Validate vendor account assignments
- Ensure payment block flags are appropriate

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BUKRS | Company Code | Direct |
| LIFNR | Vendor Number | Direct |
| BELNR | Document Number | Direct |
| GJAHR | Fiscal Year | Direct |
| BUZEI | Line Item | Direct |
| BUDAT | Posting Date | Direct |
| BLDAT | Document Date | Direct |
| ZFBDT | Baseline Date | Direct |
| ZBD1T | Days for Discount 1 | Direct |
| DMBTR | Amount in Local Currency | Direct |
| ZTERM | Payment Terms | Direct |

*Balance Reconciliation Procedures:*
- [ ] Run AP Aging Report in ECC (transaction S_ALR_87012084)
- [ ] Calculate total AP balance by company code
- [ ] Cross-check to GL reconciliation account balance
- [ ] AP Aging total must equal GL account balance (e.g., 21000 Accounts Payable)
- [ ] Variance tolerance: Zero (exact match required)

**Load Execution:**

*Migration Tool:* FI_AP_OPEN_ITEMS template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: FI_AP_OPEN_ITEMS
3. Create migration project: "WAVE3_AP_OPEN_ITEMS"
4. Upload prepared file (open invoices, credit memos)
5. Validate vendor numbers, amounts, due dates
6. Execute simulation
7. Review simulation log for errors
8. Execute final migration
9. Monitor posting log

*File Format:* CSV/Excel:
- Company Code, Vendor, Document Number, Fiscal Year, Posting Date, Due Date, Amount, Currency, Payment Terms, Discount Terms, Assignment, Reference, Text

*Key Configuration Parameters:*
- Document type: KR (Vendor Invoice) or KG (Vendor Credit Memo)
- Posting key: 31 (Vendor Invoice), 21 (Vendor Credit)
- Special GL indicator: If applicable (down payments, guarantees)
- Payment block: Retain from ECC
- Batch size: 200 documents per batch

**Pre-Import Validation:**

- [ ] All vendor numbers exist in S/4HANA
- [ ] Total AP amount matches ECC AP Aging Report
- [ ] Due dates calculated correctly
- [ ] Aging report by bucket (current, 30, 60, 90+ days) matches ECC
- [ ] Payment terms valid
- [ ] No duplicate documents
- [ ] Special GL items identified and flagged

**Post-Import Validation:**

- [ ] Run AP Aging Report in S/4HANA (transaction S_ALR_87012084)
- [ ] Compare to ECC AP Aging line-by-line
- [ ] Total AP balance: S/4HANA = ECC (zero variance required)
- [ ] Aging buckets match ECC (current, 30, 60, 90+ days)
- [ ] Sample vendor open items: Display via FBL1N, compare to ECC
- [ ] Vendor balance reconciliation: Select 10 vendors, compare total open amount
- [ ] Check due date calculations (ZBD1T, ZFBDT fields)
- [ ] Verify payment run proposal (F110) picks up open items correctly
- [ ] Test payment clearing (simulate payment, verify clearing works)
- [ ] Cross-check: AP sub-ledger total = GL reconciliation account balance (e.g., 21000)

---

### Object 28: AR Open Items

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: FBL5N (Customer Line Item Display)
- Table: BSID (Customer Open Items)
- Extract Fields: Company Code, Customer Number, Document Number, Fiscal Year, Line Item, Posting Date, Due Date, Amount, Currency, Payment Terms, Assignment
- Expected Records: All open customer invoices and credit memos as of cutoff date
- **Critical:** Balance-critical data - zero discrepancy tolerance

*Data Quality Checks:*
- [ ] All customers exist in S/4HANA (loaded in Wave 2)
- [ ] Open item amounts match AR sub-ledger
- [ ] Due dates calculated correctly
- [ ] Aging buckets correct (current, 30 days, 60 days, 90+ days)
- [ ] No cleared items included
- [ ] Partial payments accounted for correctly
- [ ] Bad debt provisions reviewed and documented

*Cleansing Rules:*
- Review old open items (>180 days) for collectability
- Write off uncollectible amounts in ECC before migration (with management approval)
- Clear small-value items (e.g., <$1) in ECC
- Validate customer account assignments
- Ensure dunning blocks are appropriate

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BUKRS | Company Code | Direct |
| KUNNR | Customer Number | Direct |
| BELNR | Document Number | Direct |
| GJAHR | Fiscal Year | Direct |
| BUZEI | Line Item | Direct |
| BUDAT | Posting Date | Direct |
| BLDAT | Document Date | Direct |
| ZFBDT | Baseline Date | Direct |
| DMBTR | Amount in Local Currency | Direct |
| ZTERM | Payment Terms | Direct |

*Balance Reconciliation Procedures:*
- [ ] Run AR Aging Report in ECC (transaction S_ALR_87012172)
- [ ] Calculate total AR balance by company code
- [ ] Cross-check to GL reconciliation account balance
- [ ] AR Aging total must equal GL account balance (e.g., 11000 Accounts Receivable)
- [ ] Variance tolerance: Zero (exact match required)

**Load Execution:**

*Migration Tool:* FI_AR_OPEN_ITEMS template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: FI_AR_OPEN_ITEMS
3. Create migration project: "WAVE3_AR_OPEN_ITEMS"
4. Upload prepared file (open invoices, credit memos)
5. Validate customer numbers, amounts, due dates
6. Execute simulation
7. Review simulation log
8. Execute final migration
9. Monitor posting log

*File Format:* CSV/Excel:
- Company Code, Customer, Document Number, Fiscal Year, Posting Date, Due Date, Amount, Currency, Payment Terms, Discount Terms, Assignment, Reference, Text

*Key Configuration Parameters:*
- Document type: DR (Customer Invoice) or DG (Customer Credit Memo)
- Posting key: 01 (Customer Invoice), 11 (Customer Credit)
- Special GL indicator: If applicable (down payments, guarantees)
- Dunning block: Retain from ECC
- Batch size: 200 documents per batch

**Pre-Import Validation:**

- [ ] All customer numbers exist in S/4HANA
- [ ] Total AR amount matches ECC AR Aging Report
- [ ] Due dates calculated correctly
- [ ] Aging report by bucket (current, 30, 60, 90+ days) matches ECC
- [ ] Payment terms valid
- [ ] No duplicate documents
- [ ] Special GL items identified and flagged

**Post-Import Validation:**

- [ ] Run AR Aging Report in S/4HANA (transaction S_ALR_87012172)
- [ ] Compare to ECC AR Aging line-by-line
- [ ] Total AR balance: S/4HANA = ECC (zero variance required)
- [ ] Aging buckets match ECC (current, 30, 60, 90+ days)
- [ ] Sample customer open items: Display via FBL5N, compare to ECC
- [ ] Customer balance reconciliation: Select 10 customers, compare total open amount
- [ ] Check due date calculations
- [ ] Verify incoming payment processing (F-28) with sample open item
- [ ] Test clearing (simulate incoming payment, verify clearing works)
- [ ] Cross-check: AR sub-ledger total = GL reconciliation account balance (e.g., 11000)

---

### Object 29: Fixed Asset Balances

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: AS03 (Display Asset), AW01N (Asset Explorer)
- Tables: ANLA (Asset Master), ANLC (Asset Values), ANLB (Depreciation Terms)
- Extract Fields: Company Code, Asset Number, Sub-number, Acquisition Value, Accumulated Depreciation, Net Book Value, Capitalization Date, Depreciation Area
- Expected Records: All active assets with non-zero values
- **Critical:** Net Book Value must reconcile to GL asset accounts

*Data Quality Checks:*
- [ ] Asset master data exists in S/4HANA (loaded in Wave 1)
- [ ] Acquisition values correct
- [ ] Accumulated depreciation accurate
- [ ] Net book value = Acquisition value - Accumulated depreciation
- [ ] Asset classes assigned correctly
- [ ] Depreciation areas configured (01-Book depreciation, 15-Tax, etc.)
- [ ] Cost center assignments valid

*Cleansing Rules:*
- Retire fully depreciated assets in ECC before migration (optional)
- Close out assets under construction (AUC) and transfer to fixed assets
- Review and correct any negative net book values
- Validate useful life and remaining life
- Ensure asset capitalization dates are accurate

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BUKRS | Company Code | Direct |
| ANLN1 | Main Asset Number | Direct |
| ANLN2 | Asset Sub-number | Direct |
| AFABER | Depreciation Area | Direct |
| ZUGDT | Capitalization Date | Direct |
| ANSWT | Acquisition Value | Direct |
| NAFAB | Posted Depreciation | Direct |
| NAFAZ | Unposted Depreciation | Calculate |

*Balance Reconciliation Procedures:*
- [ ] Run Asset Register in ECC (transaction AR01)
- [ ] Calculate total Net Book Value by company code
- [ ] Cross-check to GL asset accounts (e.g., 15000 Fixed Assets)
- [ ] Asset Net Book Value total must equal GL account balance
- [ ] Verify accumulated depreciation to GL (e.g., 16000 Accumulated Depreciation)
- [ ] Variance tolerance: Within $100 (due to rounding)

**Load Execution:**

*Migration Tool:* FI_ASSET_TRANSACTIONS template (Migration Cockpit)

*Load Steps:*
1. Asset master must be loaded first (completed in Wave 1 - Object 14)
2. Transaction: LTMC
3. Select migration object: FI_ASSET_TRANSACTIONS
4. Create migration project: "WAVE3_ASSET_BALANCES"
5. Upload asset transaction file (acquisitions, depreciation history)
6. Validate asset numbers, amounts, depreciation areas
7. Execute simulation
8. Review simulation log (check for asset not found errors)
9. Execute final migration
10. Post initial acquisition transactions
11. Post depreciation transactions to bring to current net book value

*File Format:* CSV/Excel:
- Company Code, Asset Number, Sub-number, Transaction Type (Acquisition/Depreciation), Amount, Posting Date, Depreciation Area, Cost Center, Document Text

*Key Configuration Parameters:*
- Transaction type: 100 (Acquisition), 610 (Unplanned Depreciation) to post historical depreciation
- Posting date: Original capitalization date for acquisition, cutoff date for depreciation
- Depreciation area: Load all areas (01, 15, etc.)
- Batch size: 100 assets per batch

*Batch Processing Strategy:*
- Batch 1: Post acquisition values (transaction type 100)
- Batch 2: Post accumulated depreciation (transaction type 610 or similar)
- Separate by company code

**Pre-Import Validation:**

- [ ] All asset numbers exist in S/4HANA (from Wave 1)
- [ ] Acquisition values are positive
- [ ] Accumulated depreciation values are positive
- [ ] Net book value = Acquisition - Accumulated Depreciation
- [ ] Total net book value matches ECC asset register
- [ ] Depreciation areas configured in S/4HANA
- [ ] Cost centers valid

**Post-Import Validation:**

- [ ] Run Asset Register in S/4HANA (transaction AR01)
- [ ] Compare to ECC Asset Register
- [ ] Total Net Book Value: S/4HANA = ECC (variance within $100)
- [ ] Total Acquisition Value: S/4HANA = ECC
- [ ] Total Accumulated Depreciation: S/4HANA = ECC
- [ ] Sample asset: Display in AS03, verify values match ECC
- [ ] Check asset values by depreciation area (book vs. tax)
- [ ] Verify GL account postings: Net Book Value = GL Asset Account balance
- [ ] Verify accumulated depreciation = GL Accumulated Depreciation account balance
- [ ] Test depreciation run (AFAB): Execute for sample period, verify calculation
- [ ] Check asset transactions in asset history (AB03)

---

## 3.2 Inventory & Stock

### Object 30: Inventory Stock Balances

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: MMBE (Stock Overview), MB52 (Stock List)
- Tables: MARD (Storage Location Stock), MCHB (Batch Stock), MBEW (Valuation)
- Extract Fields: Material Number, Plant, Storage Location, Batch, Unrestricted Stock Quantity, Blocked Stock, Quality Inspection Stock, Stock Value, Price Control, Standard Price/Moving Average Price
- Expected Records: All materials with non-zero stock quantities
- **Critical:** Inventory value must reconcile to GL inventory accounts (penny-level accuracy required)

*Data Quality Checks:*
- [ ] Physical inventory count completed 48 hours before cutoff
- [ ] All count variances posted and reconciled
- [ ] Material master exists in S/4HANA (loaded in Wave 2)
- [ ] Stock quantities are non-negative
- [ ] Stock value = Quantity × Price (validate calculation)
- [ ] Blocked stock and QI stock properly categorized
- [ ] No negative stock situations

*Cleansing Rules:*
- Clear all count variances before cutoff
- Write off obsolete or damaged inventory (with approval)
- Verify material numbers match S/4HANA (from Wave 2 migration)
- Ensure plant and storage location codes are valid
- Validate valuation type if split valuation used

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| MATNR | Material Number | Direct |
| WERKS | Plant | Direct |
| LGORT | Storage Location | Direct |
| CHARG | Batch | Direct (if batch-managed) |
| LABST | Unrestricted Stock | Direct |
| INSME | Quality Inspection Stock | Direct |
| SPEME | Blocked Stock | Direct |
| LBKUM | Total Stock Quantity | Sum of stock types |
| VERPR | Moving Average Price | Direct |
| STPRS | Standard Price | Direct |

*Balance Reconciliation Procedures:*
- [ ] Run Stock Value Report in ECC (transaction MB5B or MB51)
- [ ] Calculate total stock value by plant and material type
- [ ] Cross-check to GL inventory accounts (e.g., 14000 Raw Materials, 14100 Finished Goods)
- [ ] Stock value total must equal GL account balance
- [ ] Variance tolerance: Within $100 total (due to rounding)
- [ ] Review variances by material class

**Load Execution:**

*Migration Tool:* MM_STOCK template (Migration Cockpit) or MIGO (Goods Receipt for initial stock)

*Load Steps:*
1. Material master must exist (completed in Wave 2)
2. Transaction: LTMC or MIGO (for initial stock posting)
3. Select migration object: MM_STOCK
4. Create migration project: "WAVE3_INVENTORY_STOCK"
5. Upload stock balance file
6. Validate material numbers, plants, storage locations
7. Execute simulation
8. Review simulation log (check for material not found, plant not extended errors)
9. Execute final migration
10. Post stock quantities with movement type 561 (Initial Entry of Stock Balances) or use direct table load

*File Format:* CSV/Excel:
- Material Number, Plant, Storage Location, Batch, Stock Type (Unrestricted/Blocked/QI), Quantity, UOM, Value, Currency, Posting Date (cutoff date)

*Key Configuration Parameters:*
- Movement type: 561 (Initial Entry of Stock Balance) or 501 (Receipt without PO)
- Posting date: Cutoff date
- Document date: Cutoff date
- Batch size: 500 materials per batch
- Valuation: Use standard or moving average price from material master

*Batch Processing Strategy:*
- Batch 1: Unrestricted stock
- Batch 2: Blocked stock (if any)
- Batch 3: Quality inspection stock (if any)
- Separate batches by plant if large volume

**Pre-Import Validation:**

- [ ] Physical inventory count completed and reconciled
- [ ] All materials exist in S/4HANA
- [ ] All plants and storage locations configured
- [ ] Stock quantities non-negative
- [ ] Stock value calculated correctly (Quantity × Price)
- [ ] Total stock value matches ECC GL inventory accounts
- [ ] Batch numbers valid (if batch-managed materials)
- [ ] No negative stock situations

**Post-Import Validation:**

- [ ] Run Stock Overview in S/4HANA (transaction MMBE)
- [ ] Compare to ECC stock report (MB52) line-by-line
- [ ] Total stock quantity: S/4HANA = ECC for each material
- [ ] Total stock value: S/4HANA = ECC (variance within $100)
- [ ] Verify stock value by plant matches GL inventory account balance
- [ ] Sample materials: Display in MMBE, compare quantity and value to ECC
- [ ] Check stock types (unrestricted, blocked, QI) match ECC
- [ ] Verify batch stock if applicable (transaction MB53)
- [ ] Cross-check: Total inventory value = GL account balance (e.g., 14000, 14100)
- [ ] Test goods movement (MIGO): Post sample goods issue, verify stock update

---

### Object 31: Stock at Subcontractor

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: MB54 (Consignment Stock at Subcontractor)
- Table: MSKU (Subcontractor Stock)
- Extract Fields: Material Number, Plant, Vendor (Subcontractor), Quantity, Value
- Expected Records: Materials with stock at subcontractor locations
- Typically lower volume than regular inventory

*Data Quality Checks:*
- [ ] All materials exist in S/4HANA
- [ ] All vendor/subcontractor numbers exist in S/4HANA (loaded in Wave 2)
- [ ] Stock quantities reasonable and reconciled with subcontractor
- [ ] Stock value matches material price

*Cleansing Rules:*
- Confirm subcontractor stock quantities with vendors
- Write off any disputed or lost stock before migration
- Validate vendor is flagged as subcontractor in vendor master

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| MATNR | Material Number | Direct |
| WERKS | Plant | Direct |
| LIFNR | Vendor/Subcontractor | Direct |
| LABST | Stock Quantity | Direct |
| LBKUM | Total Stock | Direct |

**Load Execution:**

*Migration Tool:* MM_SUBCON_STOCK template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC
2. Select migration object: MM_SUBCON_STOCK
3. Create migration project: "WAVE3_SUBCON_STOCK"
4. Upload file
5. Execute simulation
6. Execute final migration

*Key Configuration Parameters:*
- Movement type: 541 (Subcontracting Goods Receipt - without order) for initial stock
- Posting date: Cutoff date

**Pre-Import Validation:**

- [ ] All materials exist
- [ ] All subcontractor vendor numbers exist
- [ ] Quantities reconciled with subcontractor
- [ ] Vendor is subcontractor type in vendor master

**Post-Import Validation:**

- [ ] Count of subcontractor stock records: S/4HANA = ECC
- [ ] Total quantity and value: S/4HANA = ECC
- [ ] Display sample stock in MB54
- [ ] Verify vendor assignments correct

---

### Object 32: Physical Inventory Counts

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: MI02 (Change Physical Inventory Document)
- Table: ISEG (Physical Inventory Document Items)
- Extract Fields: Physical inventory document number, material, plant, storage location, counted quantity, count date
- Expected Records: Active physical inventory documents (if any in process)
- Note: Typically, all counts should be completed and posted before cutover; this is only for in-progress counts

*Data Quality Checks:*
- [ ] All physical inventory documents should be closed before migration (preferred)
- [ ] If any open counts, review and complete in ECC if possible
- [ ] Count variances should be posted

*Cleansing Rules:*
- Complete and post all physical inventory counts before migration
- Cancel or close out any stale physical inventory documents

**Load Execution:**

*Migration Tool:* MM_PHYSICAL_INVENTORY (if needed)

*Load Steps:*
- Ideally, no load required if all counts completed in ECC
- If needed: Manually recreate open physical inventory documents in S/4HANA using transaction MI01

**Pre-Import Validation:**

- [ ] All physical inventory documents closed in ECC (preferred)
- [ ] No open counts remaining

**Post-Import Validation:**

- [ ] Verify no open physical inventory documents migrated (or only essential ones)
- [ ] Stock balances reflect posted count results

---

## 3.3 Open Procurement Documents

### Object 33: Open Purchase Orders

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: ME2N (Purchase Orders by Requisitioner)
- Tables: EKKO (PO Header), EKPO (PO Item), EKET (Scheduling Agreement Schedule Lines)
- Extract Fields: PO Number, Item Number, Vendor, Material, Quantity, Delivered Quantity, Open Quantity, Price, Currency, Delivery Date, Plant, Purchasing Organization
- Expected Records: All POs with open quantity (not fully delivered/invoiced)
- Filter: POs with open delivery quantity or invoice quantity

*Data Quality Checks:*
- [ ] Vendors exist in S/4HANA (loaded in Wave 2)
- [ ] Materials exist in S/4HANA (loaded in Wave 2)
- [ ] Purchasing info records exist (loaded in Wave 2)
- [ ] Open quantities accurate (PO quantity - delivered quantity)
- [ ] Prices match info records or are current
- [ ] Delivery dates are future-dated or reasonable

*Cleansing Rules:*
- Close out old POs (>6 months) if no longer needed (with Purchasing approval)
- Confirm delivery dates with vendors
- Update delivery schedules if needed
- Validate account assignments (cost center, GL account)

*Field Mapping:*
| ECC Field | ECC Table | S/4HANA Field | Transformation |
|-----------|-----------|---------------|----------------|
| EBELN | EKKO | PO Number | Direct or new number range |
| EBELP | EKPO | PO Item | Direct |
| LIFNR | EKKO | Vendor | Direct |
| MATNR | EKPO | Material | Direct |
| MENGE | EKPO | Order Quantity | Direct |
| WEMNG | EKPO | Goods Receipt Quantity | Direct |
| NETPR | EKPO | Net Price | Direct |
| EINDT | EKET | Delivery Date | Direct |
| WERKS | EKPO | Plant | Direct |
| EKORG | EKKO | Purchasing Organization | Direct |

*Balance Reconciliation Procedures:*
- [ ] Run Open PO Report in ECC (transaction ME2N or ME80FN)
- [ ] Calculate total open PO value by purchasing organization
- [ ] Note: POs don't have GL balance impact until GR or invoice, so no GL reconciliation needed
- [ ] However, verify GR/IR clearing account balance matches expectation (goods received but not invoiced)

**Load Execution:**

*Migration Tool:* MM_PURCHASE_ORDER template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC or ME21N (manual creation for complex POs)
2. Select migration object: MM_PURCHASE_ORDER
3. Create migration project: "WAVE3_OPEN_PO"
4. Upload prepared file
5. Validate vendor, material, info record references
6. Execute simulation
7. Review simulation log (check for missing vendor/material errors)
8. Execute final migration
9. Monitor PO creation log

*File Format:* CSV/Excel:
- PO Number (optional - can auto-generate), Vendor, Material, Order Quantity, Delivered Quantity, Price, Currency, Delivery Date, Plant, Purchasing Organization, Account Assignment (Cost Center/GL Account)

*Key Configuration Parameters:*
- Document type: NB (Standard PO) or others as appropriate
- PO number: Can retain ECC PO number (if S/4HANA allows external numbering) or assign new
- Item category: Standard, subcontracting, service, etc.
- Account assignment: K (Cost Center), S (Sales Order), etc.
- Batch size: 100 POs per batch

*Batch Processing Strategy:*
- Batch 1: Standard POs
- Batch 2: Subcontracting POs
- Batch 3: Service POs

**Pre-Import Validation:**

- [ ] All vendors exist in S/4HANA
- [ ] All materials exist in S/4HANA
- [ ] Open quantities calculated correctly (ordered - delivered)
- [ ] Prices are reasonable and match info records (where applicable)
- [ ] Delivery dates are future-dated or within reasonable past
- [ ] Account assignments valid (cost centers, GL accounts exist)
- [ ] No POs with zero open quantity

**Post-Import Validation:**

- [ ] Run Open PO Report in S/4HANA (transaction ME2N or ME80FN)
- [ ] Compare to ECC Open PO Report
- [ ] Total open PO quantity: S/4HANA = ECC for each material
- [ ] Total open PO value: S/4HANA = ECC
- [ ] Sample POs: Display via ME23N, compare to ECC
- [ ] Verify PO item details (quantity, price, delivery date)
- [ ] Check delivery schedules (transaction ME38)
- [ ] Test PO processing: Create goods receipt (MIGO) for sample PO item
- [ ] Verify PO history updated correctly after test GR

---

### Object 34: Open Purchase Requisitions

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: ME5A (Purchase Requisitions List)
- Table: EBAN (Purchase Requisition)
- Extract Fields: PR Number, Item Number, Material, Quantity, Requested Date, Requisitioner, Plant, Cost Center/GL Account
- Expected Records: PRs not yet fully converted to PO or deleted
- Filter: PR items not deleted and not fully assigned to PO

*Data Quality Checks:*
- [ ] Materials exist in S/4HANA
- [ ] Requested delivery dates reasonable
- [ ] Account assignments valid
- [ ] Requisitioners exist (user IDs or cost centers)

*Cleansing Rules:*
- Delete old PRs (>90 days) if no longer needed
- Update delivery dates if needed
- Validate account assignments

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| BANFN | PR Number | Direct or new number range |
| BNFPO | PR Item | Direct |
| MATNR | Material | Direct |
| MENGE | Quantity | Direct |
| LFDAT | Delivery Date | Direct |
| AFNAM | Requisitioner | Direct |
| WERKS | Plant | Direct |
| KOSTL | Cost Center | Direct (if account assignment) |

**Load Execution:**

*Migration Tool:* MM_PURCHASE_REQ template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC or ME51N (manual creation)
2. Select migration object: MM_PURCHASE_REQ
3. Create migration project: "WAVE3_OPEN_PR"
4. Upload file
5. Execute simulation
6. Execute final migration

*Key Configuration Parameters:*
- Document type: NB (Standard PR)
- Item category: Standard, stock transfer, subcontracting
- Batch size: 200 PRs per batch

**Pre-Import Validation:**

- [ ] All materials exist
- [ ] Quantities positive
- [ ] Delivery dates reasonable
- [ ] Account assignments valid

**Post-Import Validation:**

- [ ] Run PR List in S/4HANA (transaction ME5A)
- [ ] Compare to ECC PR List
- [ ] Total open PR quantity: S/4HANA = ECC
- [ ] Sample PRs: Display via ME53N, compare to ECC
- [ ] Test PR conversion: Convert sample PR to PO (ME57)

---

## 3.4 Open Sales Documents

### Object 35: Open Sales Orders

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: VA05 (List of Sales Orders)
- Tables: VBAK (Sales Document Header), VBAP (Sales Document Item), VBUK (Sales Document Header Status)
- Extract Fields: Sales Order Number, Item Number, Customer, Material, Order Quantity, Delivered Quantity, Open Quantity, Net Value, Currency, Requested Delivery Date, Plant, Sales Organization
- Expected Records: Sales orders with open delivery quantity
- Filter: Overall delivery status not complete

*Data Quality Checks:*
- [ ] Customers exist in S/4HANA (loaded in Wave 2)
- [ ] Materials exist in S/4HANA (loaded in Wave 2)
- [ ] Customer pricing conditions exist (loaded in Wave 2)
- [ ] Open quantities accurate (ordered - delivered)
- [ ] Pricing conditions applied correctly
- [ ] Requested delivery dates reasonable

*Cleansing Rules:*
- Close out old sales orders (>6 months) if no longer needed (with Sales approval)
- Confirm delivery dates with customers
- Update pricing if needed
- Validate credit check status

*Field Mapping:*
| ECC Field | ECC Table | S/4HANA Field | Transformation |
|-----------|-----------|---------------|----------------|
| VBELN | VBAK | Sales Order Number | Direct or new number range |
| POSNR | VBAP | Item Number | Direct |
| KUNNR | VBAK | Sold-to Customer | Direct |
| MATNR | VBAP | Material | Direct |
| KWMENG | VBAP | Order Quantity | Direct |
| LFIMG | VBAP | Delivered Quantity | Calculate from LIPS |
| NETWR | VBAP | Net Value | Direct |
| EDATU | VBAP | Requested Delivery Date | Direct |
| WERKS | VBAP | Plant | Direct |
| VKORG | VBAK | Sales Organization | Direct |

*Balance Reconciliation Procedures:*
- [ ] Run Open Sales Orders Report in ECC (transaction VA05)
- [ ] Calculate total open SO value by sales organization
- [ ] Note: No GL impact until delivery/billing, so no GL reconciliation needed

**Load Execution:**

*Migration Tool:* SD_SALES_ORDER template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC or VA01 (manual creation for complex orders)
2. Select migration object: SD_SALES_ORDER
3. Create migration project: "WAVE3_OPEN_SO"
4. Upload prepared file
5. Validate customer, material, pricing references
6. Execute simulation
7. Review simulation log
8. Execute final migration
9. Monitor SO creation log

*File Format:* CSV/Excel:
- Sales Order Number (optional), Customer, PO Number, Order Date, Material, Order Quantity, Delivered Quantity, Requested Delivery Date, Plant, Sales Organization, Pricing Condition

*Key Configuration Parameters:*
- Document type: OR (Standard Order) or others as appropriate
- Sales order number: Can retain ECC SO number or assign new
- Item category: TAN (Standard), TAD (Service), etc.
- Pricing: Automatic determination from conditions
- Batch size: 100 SOs per batch

**Pre-Import Validation:**

- [ ] All customers exist in S/4HANA
- [ ] All materials exist in S/4HANA
- [ ] Open quantities calculated correctly (ordered - delivered)
- [ ] Pricing conditions available
- [ ] Delivery dates reasonable
- [ ] No SOs with zero open quantity

**Post-Import Validation:**

- [ ] Run Open Sales Orders Report in S/4HANA (transaction VA05)
- [ ] Compare to ECC Open SO Report
- [ ] Total open SO quantity: S/4HANA = ECC for each material
- [ ] Total open SO value: S/4HANA = ECC
- [ ] Sample SOs: Display via VA03, compare to ECC
- [ ] Verify SO item details (quantity, price, delivery date)
- [ ] Check pricing (transaction VA02, pricing tab)
- [ ] Test SO processing: Create delivery (VL01N) for sample SO item
- [ ] Verify SO status updated correctly after test delivery

---

### Object 36: Sales Contracts

**Data Preparation & Cleansing:**

*ECC Extraction:*
- Transaction: VA45 (List of Contracts)
- Tables: VBAK (Sales Document Header), VBAP (Sales Document Item)
- Extract Fields: Contract Number, Item Number, Customer, Material, Target Quantity, Released Quantity, Contract Value, Valid From, Valid To
- Expected Records: Active contracts (not expired)
- Filter: Valid To date in future

*Data Quality Checks:*
- [ ] Customers exist in S/4HANA
- [ ] Materials exist in S/4HANA (if material-specific contracts)
- [ ] Validity dates accurate
- [ ] Target quantities reasonable
- [ ] Released quantities accurate

*Cleansing Rules:*
- Close expired contracts in ECC before migration
- Update validity dates if needed
- Validate pricing in contracts

*Field Mapping:*
| ECC Field | S/4HANA Field | Transformation |
|-----------|---------------|----------------|
| VBELN | Contract Number | Direct or new number range |
| POSNR | Item Number | Direct |
| KUNNR | Sold-to Customer | Direct |
| MATNR | Material | Direct (if applicable) |
| KWMENG | Target Quantity | Direct |
| KBMENG | Released Quantity | Direct |
| NETWR | Contract Value | Direct |
| GUEBG | Valid From | Direct |
| GUEEN | Valid To | Direct |

**Load Execution:**

*Migration Tool:* SD_CONTRACT template (Migration Cockpit)

*Load Steps:*
1. Transaction: LTMC or VA41 (manual creation)
2. Select migration object: SD_CONTRACT
3. Create migration project: "WAVE3_SALES_CONTRACT"
4. Upload file
5. Execute simulation
6. Execute final migration

*Key Configuration Parameters:*
- Document type: K (Contract), WK1 (Value Contract), etc.
- Contract number: Retain or assign new
- Batch size: 50 contracts per batch

**Pre-Import Validation:**

- [ ] All customers exist
- [ ] All materials exist (if applicable)
- [ ] Validity dates logical (Valid To > Valid From)
- [ ] Target quantities positive

**Post-Import Validation:**

- [ ] Run Contracts List in S/4HANA (transaction VA45)
- [ ] Compare to ECC Contracts List
- [ ] Total contract count: S/4HANA = ECC
- [ ] Sample contracts: Display via VA43, compare to ECC
- [ ] Verify contract details (validity, quantities, pricing)
- [ ] Test contract release: Create sales order referencing contract (VA01)

---

## Wave 3 Load Sequence

Execute Wave 3 objects in the following sequence, respecting dependencies and balance criticality:

### Phase 1: Financial Balances (Day 1 Morning - Critical Path)

**Timing:** 4-6 hours  
**Critical:** This is the most critical phase - all balances must reconcile to zero variance

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 1.1 | GL Account Balances | FI_BALANCE / ACDOCA | 2-3 hrs | Wave 1 GL Accounts | [ ] |
| 1.2 | GL Open Line Items | FI_GL_OPEN_ITEMS | 1-2 hrs | GL Accounts (1.1) | [ ] |

**Phase 1 Checkpoint:**
- [ ] Trial Balance: S/4HANA = ECC (zero variance)
- [ ] Balance Sheet balances
- [ ] GL open items loaded
- [ ] Finance Lead sign-off on balances

### Phase 2: Sub-Ledger Open Items (Day 1 Afternoon - Critical Path)

**Timing:** 4-6 hours  
**Critical:** AP/AR aging must match ECC exactly

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 2.1 | AP Open Items | FI_AP_OPEN_ITEMS | 2-3 hrs | Vendors (Wave 2), GL Balances (1.1) | [ ] |
| 2.2 | AR Open Items | FI_AR_OPEN_ITEMS | 2-3 hrs | Customers (Wave 2), GL Balances (1.1) | [ ] |

**Phase 2 Checkpoint:**
- [ ] AP Aging: S/4HANA = ECC (zero variance)
- [ ] AR Aging: S/4HANA = ECC (zero variance)
- [ ] AP sub-ledger = GL reconciliation account
- [ ] AR sub-ledger = GL reconciliation account
- [ ] Finance Lead sign-off

### Phase 3: Asset Balances (Day 1 Evening - Can Overlap with Phase 2)

**Timing:** 3-4 hours  
**Critical:** Net Book Value must equal GL asset accounts

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 3.1 | Fixed Asset Balances | FI_ASSET_TRANSACTIONS | 3-4 hrs | Asset Master (Wave 1), GL Balances (1.1) | [ ] |

**Phase 3 Checkpoint:**
- [ ] Asset Net Book Value = ECC (variance within $100)
- [ ] Asset Net Book Value = GL Asset Accounts
- [ ] Accumulated Depreciation = GL Accumulated Depreciation Account
- [ ] Finance Lead sign-off

### Phase 4: Inventory Balances (Day 2 Morning - Critical Path)

**Timing:** 4-6 hours  
**Critical:** Inventory value must reconcile to penny level

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 4.1 | Inventory Stock Balances | MM_STOCK | 4-5 hrs | Material Master (Wave 2), Physical Count Complete | [ ] |
| 4.2 | Stock at Subcontractor | MM_SUBCON_STOCK | 1 hr | Material Master (Wave 2), Vendors (Wave 2) | [ ] |
| 4.3 | Physical Inventory Counts | MM_PHYSICAL_INVENTORY | 30 min | Material Master (Wave 2) | [ ] |

**Phase 4 Checkpoint:**
- [ ] Stock quantities: S/4HANA = ECC for all materials
- [ ] Stock value: S/4HANA = ECC (variance within $100)
- [ ] Stock value = GL Inventory Accounts
- [ ] Subcontractor stock reconciled
- [ ] MM Lead sign-off

### Phase 5: Open Procurement Documents (Day 2 Afternoon - Can Run Parallel)

**Timing:** 3-4 hours  
**Note:** Not balance-critical, but important for operations

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 5.1 | Open Purchase Orders | MM_PURCHASE_ORDER | 2-3 hrs | Vendors (Wave 2), Materials (Wave 2), Info Records (Wave 2) | [ ] |
| 5.2 | Open Purchase Requisitions | MM_PURCHASE_REQ | 1 hr | Materials (Wave 2) | [ ] |

**Phase 5 Checkpoint:**
- [ ] Open PO count and value match ECC
- [ ] Open PR count and value match ECC
- [ ] MM Lead sign-off

### Phase 6: Open Sales Documents (Day 2 Afternoon - Can Run Parallel with Phase 5)

**Timing:** 3-4 hours  
**Note:** Not balance-critical, but important for operations

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 6.1 | Open Sales Orders | SD_SALES_ORDER | 2-3 hrs | Customers (Wave 2), Materials (Wave 2), Pricing (Wave 2) | [ ] |
| 6.2 | Sales Contracts | SD_CONTRACT | 1 hr | Customers (Wave 2), Materials (Wave 2) | [ ] |

**Phase 6 Checkpoint:**
- [ ] Open SO count and value match ECC
- [ ] Sales contracts loaded
- [ ] SD Lead sign-off

### Phase 7: Final Validation & Go-Live Preparation (Day 2 Evening)

**Timing:** 2-3 hours

| Step | Activity | Duration | Status |
|------|----------|----------|--------|
| 7.1 | Run all final reconciliation reports | 1 hr | [ ] |
| 7.2 | Complete validation checklists | 1 hr | [ ] |
| 7.3 | Obtain final sign-offs from all leads | 30 min | [ ] |
| 7.4 | Prepare Go-Live readiness report | 30 min | [ ] |
| 7.5 | Go/No-Go decision meeting | As needed | [ ] |

---

## Validation & Sign-Off Checklist

### Financial Balances Validation

#### GL Account Balances
- [ ] Trial Balance reconciliation complete
- [ ] Debit total: S/4HANA = ECC
- [ ] Credit total: S/4HANA = ECC
- [ ] Variance: Zero (no tolerance)
- [ ] Balance Sheet total: S/4HANA = ECC
- [ ] P&L accounts reconciled (if mid-year cutover)
- [ ] Cost center balances match
- [ ] Profit center balances match
- [ ] Segment balances match (if applicable)
- [ ] All company codes reconciled (7 company codes)

**Reconciliation Table:**
| Company Code | ECC Debit Total | ECC Credit Total | S/4HANA Debit Total | S/4HANA Credit Total | Variance | Status |
|--------------|-----------------|------------------|---------------------|----------------------|----------|--------|
| SG21 | | | | | | [ ] |
| CN13 | | | | | | [ ] |
| CN17 | | | | | | [ ] |
| US10 | | | | | | [ ] |
| BE10 | | | | | | [ ] |
| HCIL | | | | | | [ ] |
| BR10 | | | | | | [ ] |

**Sign-Off:**
- [ ] FI Lead: _________________ Date: _______

#### GL Open Line Items
- [ ] Open item count: S/4HANA = ECC
- [ ] Total open item value reconciled
- [ ] Sample open items verified (10% sample)
- [ ] Clearing functionality tested

**Sign-Off:**
- [ ] FI Lead: _________________ Date: _______

#### AP Open Items
- [ ] AP Aging Report: S/4HANA = ECC
- [ ] Total AP balance: S/4HANA = ECC (zero variance)
- [ ] Aging buckets match:
  - [ ] Current (0-30 days)
  - [ ] 31-60 days
  - [ ] 61-90 days
  - [ ] 90+ days
- [ ] AP sub-ledger = GL reconciliation account (e.g., 21000)
- [ ] Sample vendor balances verified (10 vendors)
- [ ] Due date calculations correct
- [ ] Payment run tested with sample vendor

**Reconciliation Table:**
| Company Code | ECC Total AP | S/4HANA Total AP | Variance | GL Account Balance | Variance to GL | Status |
|--------------|--------------|------------------|----------|--------------------|--------------------|--------|
| SG21 | | | | | | [ ] |
| CN13 | | | | | | [ ] |
| CN17 | | | | | | [ ] |
| US10 | | | | | | [ ] |
| BE10 | | | | | | [ ] |
| HCIL | | | | | | [ ] |
| BR10 | | | | | | [ ] |

**Sign-Off:**
- [ ] FI Lead: _________________ Date: _______

#### AR Open Items
- [ ] AR Aging Report: S/4HANA = ECC
- [ ] Total AR balance: S/4HANA = ECC (zero variance)
- [ ] Aging buckets match:
  - [ ] Current (0-30 days)
  - [ ] 31-60 days
  - [ ] 61-90 days
  - [ ] 90+ days
- [ ] AR sub-ledger = GL reconciliation account (e.g., 11000)
- [ ] Sample customer balances verified (10 customers)
- [ ] Due date calculations correct
- [ ] Incoming payment tested with sample customer

**Reconciliation Table:**
| Company Code | ECC Total AR | S/4HANA Total AR | Variance | GL Account Balance | Variance to GL | Status |
|--------------|--------------|------------------|----------|--------------------|--------------------|--------|
| SG21 | | | | | | [ ] |
| CN13 | | | | | | [ ] |
| CN17 | | | | | | [ ] |
| US10 | | | | | | [ ] |
| BE10 | | | | | | [ ] |
| HCIL | | | | | | [ ] |
| BR10 | | | | | | [ ] |

**Sign-Off:**
- [ ] FI Lead: _________________ Date: _______

#### Fixed Asset Balances
- [ ] Asset Net Book Value: S/4HANA = ECC (variance within $100)
- [ ] Total Acquisition Value: S/4HANA = ECC
- [ ] Total Accumulated Depreciation: S/4HANA = ECC
- [ ] Asset Net Book Value = GL Asset Accounts
- [ ] Accumulated Depreciation = GL Accumulated Depreciation Account
- [ ] Sample assets verified (10% sample)
- [ ] Depreciation run tested

**Reconciliation Table:**
| Company Code | ECC Net Book Value | S/4HANA Net Book Value | Variance | GL Asset Account | GL Accum Depr Account | Status |
|--------------|---------------------|------------------------|----------|-------------------|-----------------------|--------|
| SG21 | | | | | | [ ] |
| CN13 | | | | | | [ ] |
| CN17 | | | | | | [ ] |
| US10 | | | | | | [ ] |
| BE10 | | | | | | [ ] |
| HCIL | | | | | | [ ] |
| BR10 | | | | | | [ ] |

**Sign-Off:**
- [ ] FI Lead: _________________ Date: _______

### Inventory Balances Validation

#### Inventory Stock Balances
- [ ] Physical inventory count completed and posted
- [ ] Stock quantities: S/4HANA = ECC (all materials)
- [ ] Stock value: S/4HANA = ECC (variance within $100)
- [ ] Stock value = GL Inventory Accounts
- [ ] Stock breakdown by plant matches ECC
- [ ] Stock breakdown by material type matches ECC
- [ ] Blocked stock correctly categorized
- [ ] Quality inspection stock correctly categorized
- [ ] Sample materials verified (15% sample)
- [ ] Goods movement tested (MIGO)

**Reconciliation Table:**
| Plant | Material Type | ECC Quantity | ECC Value | S/4HANA Quantity | S/4HANA Value | Variance | GL Account Balance | Status |
|-------|---------------|--------------|-----------|------------------|---------------|----------|--------------------|--------|
| | Raw Materials | | | | | | 14000 | [ ] |
| | Semifinished | | | | | | 14100 | [ ] |
| | Finished Goods | | | | | | 14200 | [ ] |

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______

#### Stock at Subcontractor
- [ ] Subcontractor stock count: S/4HANA = ECC
- [ ] Subcontractor stock value: S/4HANA = ECC
- [ ] Vendor assignments correct

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______

#### Physical Inventory Counts
- [ ] All physical inventory documents closed (preferred)
- [ ] No open counts remaining (or only essential)

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______

### Open Procurement Documents Validation

#### Open Purchase Orders
- [ ] Open PO count: S/4HANA = ECC
- [ ] Total open PO value: S/4HANA = ECC
- [ ] Open PO quantity by material: S/4HANA = ECC
- [ ] Sample POs verified (10% sample)
- [ ] PO processing tested (goods receipt)

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______

#### Open Purchase Requisitions
- [ ] Open PR count: S/4HANA = ECC
- [ ] Total open PR value: S/4HANA = ECC
- [ ] Sample PRs verified
- [ ] PR conversion to PO tested

**Sign-Off:**
- [ ] MM Lead: _________________ Date: _______

### Open Sales Documents Validation

#### Open Sales Orders
- [ ] Open SO count: S/4HANA = ECC
- [ ] Total open SO value: S/4HANA = ECC
- [ ] Open SO quantity by material: S/4HANA = ECC
- [ ] Sample SOs verified (10% sample)
- [ ] SO processing tested (delivery creation)

**Sign-Off:**
- [ ] SD Lead: _________________ Date: _______

#### Sales Contracts
- [ ] Contract count: S/4HANA = ECC
- [ ] Sample contracts verified
- [ ] Contract release tested

**Sign-Off:**
- [ ] SD Lead: _________________ Date: _______

### Integration & System Validation

- [ ] End-to-end financial posting tested (GL, AP, AR)
- [ ] End-to-end procurement process tested (PR → PO → GR → Invoice)
- [ ] End-to-end sales process tested (SO → Delivery → Invoice)
- [ ] Period-end closing procedures tested
- [ ] Financial reporting tested (Trial Balance, P&L, Balance Sheet)
- [ ] Inventory reporting tested (Stock Overview, Stock Value)
- [ ] AP/AR reporting tested (Aging Reports, Payment Reports)
- [ ] User access and authorizations verified
- [ ] Interfaces to external systems tested

**Sign-Off:**
- [ ] Integration Lead: _________________ Date: _______

### Mock Cutover vs Final Cutover

**Mock Cutover Completion (T-2 weeks):**
- [ ] All Wave 3 objects loaded in sandbox/QA system
- [ ] Full validation completed
- [ ] Timing validated (did we meet 2-day target?)
- [ ] Issues logged and remediation plan created
- [ ] Team training completed
- [ ] Runbook updated based on lessons learned

**Final Cutover Readiness:**
- [ ] Mock cutover successful (all balances reconciled)
- [ ] All mock cutover issues resolved
- [ ] Final cutoff date confirmed with business
- [ ] Data freeze communication sent to all users
- [ ] ECC system backup scheduled
- [ ] S/4HANA system locked for migration
- [ ] Rollback plan tested and ready
- [ ] Go-Live communication prepared

### Final Wave 3 Sign-Off

**Critical Success Criteria (Go/No-Go):**
- [ ] GL Trial Balance: Zero variance
- [ ] AP Aging: Zero variance
- [ ] AR Aging: Zero variance
- [ ] Inventory Value: Within $100 variance
- [ ] Asset Net Book Value: Within $100 variance
- [ ] All open documents loaded and verified
- [ ] All functional testing passed
- [ ] No critical errors remaining in migration logs

**Overall Wave 3 Sign-Off:**
- [ ] Data Migration Lead: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______
- [ ] MM Lead: _________________ Date: _______
- [ ] SD Lead: _________________ Date: _______
- [ ] Project Manager: _________________ Date: _______

**Go-Live Decision:**
- [ ] **GO** - Proceed with Go-Live
- [ ] **NO-GO** - Defer Go-Live (specify reason and revised date)

**If No-Go, Outstanding Items:**
1. ___________________________________________________________
2. ___________________________________________________________
3. ___________________________________________________________

**Revised Go-Live Date (if applicable):** ___________________

---

## Troubleshooting Quick Reference

### Common Issues - Financial Data

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Trial Balance doesn't match | Data extraction error, wrong cutoff date, missing postings | Re-extract data from ECC with correct date, verify all periods posted | FI Lead |
| AP/AR Aging doesn't match | Cleared items included, partial payments missing, currency conversion error | Filter for open items only (AUGBL blank), check partial payment postings | FI Lead |
| GL balance variance | Rounding differences, cost center/profit center mismatch, period assignment error | Review line-item details, check aggregation logic, verify period assignment | FI Lead |
| Asset balance variance | Depreciation calculation difference, acquisition date mismatch, depreciation area mismatch | Verify depreciation run dates, check acquisition transaction dates, validate areas | FI Lead |
| Posting period closed | Period not open in S/4HANA | Open posting period in S/4HANA (OB52), use special period for opening balances | FI Lead / Basis |

### Common Issues - Inventory Data

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Stock value doesn't match | Price difference, quantity variance, valuation method mismatch | Verify material prices (standard vs. moving average), recount quantities, check valuation type | MM Lead / FI Lead |
| Negative stock | Data error, goods movements not posted, stock transfer in-transit | Review material movements, post missing GRs/GIs, check stock transfer status | MM Lead |
| Material not found | Material not migrated in Wave 2, material number mismatch | Verify material exists in S/4HANA, check material number mapping | MM Lead |
| Storage location error | Storage location not extended to plant, storage location not configured | Extend storage location to plant in material master (MM02), configure storage location | MM Lead |
| Batch stock error | Batch not created, batch classification missing | Create batch in S/4HANA (MSC1N), verify batch characteristics | MM Lead |

### Common Issues - Open Documents

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| PO load fails - vendor not found | Vendor not migrated in Wave 2, vendor number mismatch | Verify vendor exists in S/4HANA, check vendor number mapping | MM Lead |
| PO load fails - material not found | Material not migrated in Wave 2, material not extended to plant | Verify material exists, extend to plant in material master | MM Lead |
| PO price different from info record | Info record not loaded or price mismatch | Load/update info record, or accept PO-specific price | MM Lead |
| SO load fails - customer not found | Customer not migrated in Wave 2, customer not extended to sales org | Verify customer exists, extend to sales org in customer master | SD Lead |
| SO pricing error | Pricing conditions not loaded, pricing procedure mismatch | Load pricing conditions (Wave 2), verify pricing procedure configuration | SD Lead |
| SO credit check failure | Credit limit not set, credit control area not assigned | Set credit limit (FD32), assign credit control area to customer | SD Lead / FI Lead |

### Common Issues - Balance Reconciliation

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Sub-ledger doesn't equal GL | Reconciliation account mismatch, posting to wrong account, manual GL postings in ECC | Review reconciliation account assignments, check for direct GL postings (should go through sub-ledger) | FI Lead |
| Aging report incorrect | Due date calculation error, baseline date wrong, payment terms mismatch | Verify payment terms, check baseline date (ZFBDT), recalculate due dates | FI Lead |
| Open item clearing doesn't work | Assignment field blank, document number mismatch | Populate assignment field (ZUONR), ensure document numbers match for clearing | FI Lead |
| Currency translation difference | Exchange rate difference, translation date mismatch | Verify exchange rates, check translation date settings | FI Lead |

### Escalation Path

| Level | Contact | Response Time | Issues Handled |
|-------|---------|---------------|----------------|
| **Level 1: Technical Team** | Migration Team Members | Immediate | Data format errors, file upload issues, standard migration errors |
| **Level 2: Functional Leads** | FI/MM/SD Leads | 30 minutes | Reconciliation issues, balance variances, functional validation failures |
| **Level 3: Project Manager** | Project Manager | 1 hour | Critical blockers, go/no-go decisions, timeline issues |
| **Level 4: Executive Sponsor** | Executive Sponsor | 2 hours | Go-Live deferral, major data issues requiring business decision |

### Key Contacts (Wave 3 Critical)

| Role | Name | Email | Phone | Availability |
|------|------|-------|-------|--------------|
| Data Migration Lead | TBD | TBD | TBD | 24/7 during Wave 3 |
| FI Lead | Frey Zheng | TBD | TBD | 24/7 during Wave 3 |
| MM Lead | Meos Xu | TBD | TBD | 24/7 during Wave 3 |
| SD Lead | Warner Yu | TBD | TBD | 24/7 during Wave 3 |
| Project Manager | TBD | TBD | TBD | 24/7 during Wave 3 |
| SAP Basis Support | TBD | TBD | TBD | 24/7 |
| Executive Sponsor | TBD | TBD | TBD | On-call during cutover |

### Useful Transaction Codes

#### Financial Transactions
- `FAGLB03` - GL Account Balances
- `FBL3N` - GL Account Line Items
- `FBL1N` - Vendor Line Items
- `FBL5N` - Customer Line Items
- `FB03` - Display Document
- `FB50` - GL Posting
- `F110` - Payment Run
- `F-28` - Incoming Payments
- `F-03` - Clear GL Account
- `S_ALR_87012084` - AP Aging Report
- `S_ALR_87012172` - AR Aging Report

#### Asset Accounting
- `AS03` - Display Asset
- `AW01N` - Asset Explorer
- `AR01` - Asset Register
- `AB03` - Asset History
- `AFAB` - Depreciation Run

#### Inventory Management
- `MMBE` - Stock Overview
- `MB52` - Stock List
- `MB5B` - Stock Value Report
- `MB54` - Stock at Subcontractor
- `MIGO` - Goods Movement
- `MI02` - Change Physical Inventory Document

#### Purchasing
- `ME23N` - Display Purchase Order
- `ME2N` - Purchase Orders by Requisitioner
- `ME80FN` - Open PO Report
- `ME53N` - Display Purchase Requisition
- `ME5A` - Purchase Requisitions List

#### Sales
- `VA03` - Display Sales Order
- `VA05` - List of Sales Orders
- `VA43` - Display Contract
- `VA45` - List of Contracts
- `VL01N` - Create Delivery

#### Migration & System
- `LTMC` - Migration Cockpit
- `SM37` - Job Overview
- `SM50` - Process Overview
- `OB52` - Open/Close Posting Periods
- `SLG1` - Application Log

---

## Document Control

**Version History:**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 2025 | Data Migration Team | Initial comprehensive Wave 3 runbook |

**Approval:**

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Data Migration Lead | TBD | | |
| FI Lead | Frey Zheng | | |
| MM Lead | Meos Xu | | |
| SD Lead | Warner Yu | | |
| Project Manager | TBD | | |

---

**End of Wave 3 Execution Runbook**

**Critical Reminder:**
Wave 3 is the most critical wave - zero balance variance tolerance. Do not proceed to Go-Live unless ALL financial balances reconcile exactly and ALL validation checklists are complete.

**Next Steps:**
- Upon completion of Wave 3 validation and sign-off
- Obtain Go-Live approval from Executive Sponsor
- Communicate Go-Live readiness to business users
- Proceed with Go-Live cutover
