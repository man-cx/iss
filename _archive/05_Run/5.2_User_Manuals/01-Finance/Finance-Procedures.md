# Finance Department - SAP Procedures
## Home Control SAP S/4HANA

---

## GENERAL LEDGER PROCEDURES

### 1. POST GL JOURNAL ENTRY

**Application:** Manage Journal Entries

**Example:** Record January utilities accrual for CN13 factory ($10,000)

**Steps:**
1. Open **Manage Journal Entries** → Click "Create"
2. Enter:
   - Company Code: **CN13** (or SG21, CN17, BE10, US10)
   - Posting Date: **2025-01-31** (last day of month for accruals)
   - Document Date: Today's date
   - Reference: Utility invoice number if available
   - Header Text: "Jan 2025 Utilities Accrual"

3. **Debit Line** (Expense):
   - GL Account: **65001** (Utilities Expense)
   - Amount: **10000**
   - Cost Center: **CN13SG1** (your department's cost center)
   - Text: "Jan utilities accrual"

4. **Credit Line** (Liability):
   - GL Account: **21001** (Accrued Expenses)
   - Amount: **10000**
   - Text: "Jan utilities accrual"

5. Verify Balance = **0.00** (debits = credits)
6. Click "Check" → Wait for green message
7. Click "Post" → Save document number (e.g., **1900000123**)
8. File document number with supporting paperwork

**Common Company Codes at Home Control:**
- SG21 = Singapore HQ
- CN13 = Suzhou factory
- CN17 = Shanghai office  
- BE10 = Belgium
- US10 = USA

**Common Cost Centers:**
- CN13MF1 = Manufacturing (Suzhou)
- CN13QC1 = Quality Control (Suzhou)
- SG21SA1 = Sales (Singapore)
- SG21FI1 = Finance (Singapore)

---

### 2. REVERSE INCORRECT JOURNAL ENTRY

**Example:** You posted document 1900000123 with wrong amount, need to reverse it

**Steps:**
1. Open **Manage Journal Entries**
2. Click "Reverse" function
3. Enter document number to reverse: **1900000123**
4. Enter reversal reason: "Wrong amount posted"
5. Reversal date: Today (or specify if backdating)
6. Click "Post"
7. System creates reversal document (negative of original)
8. Create new correct journal entry
9. Document both in your records

---

### 3. MONTH-END CLOSE - GL PROCESSING

**Timeline:** Day 1-3 after month end

**Your Tasks:**

**Day 1 (After Month End):**
1. Open **Display G/L Account Balances**
2. Check all parked documents cleared:
   - Company Code: Your code
   - Status: Parked
   - If any found, either post or delete them
3. Verify all recurring entries posted (rent, insurance, etc.)

**Day 2:**
1. Post month-end accruals (utilities, salaries, etc.)
2. Post any manual adjustments
3. Run preliminary reports to check for errors

**Day 3:**
1. Final review of all GL postings
2. Notify GL Executive Periodic when ready to close
3. After close, no more postings allowed to prior month

---

## ACCOUNTS PAYABLE PROCEDURES

### 4. POST VENDOR INVOICE (No PO)

**Application:** Create Incoming Invoices

**Example:** Post office supply invoice from vendor 1000567 for $250

**Steps:**
1. Open **Create Incoming Invoices**
2. Enter header:
   - Company Code: **SG21**
   - Vendor: **1000567** (your supplier number)
   - Invoice Date: Date on vendor invoice (e.g., 2025-01-15)
   - Posting Date: Usually today
   - Amount: **250.00**
   - Currency: **SGD** (or CNY for China)
   - Reference: **Vendor invoice number** (MUST enter!)

3. Enter line item:
   - GL Account: **60201** (Office Supplies Expense)
   - Amount: **250.00**
   - Cost Center: **SG21FI1** (Finance Singapore)
   - Tax Code: **P9** (9% input tax for Singapore)
   - Text: "Office supplies - Jan 2025"

4. System calculates:
   - Net: 250.00
   - Tax: 22.50
   - Gross: 272.50
   - Vendor payable: 272.50

5. Click "Check" → Click "Post"
6. Save document number
7. Attach scanned invoice to document in system or file folder

**Common Expense GL Accounts:**
- 60201 = Office Supplies
- 65001 = Utilities
- 66001 = Travel Expense
- 67001 = Professional Fees
- 68001 = Repairs & Maintenance

**Tax Codes:**
- **Singapore:** P9 (9% purchase tax), P0 (0% tax)
- **China:** J2 (13%), J4 (6%), J0 (0%)

---

### 5. RUN PAYMENT PROPOSAL FOR VENDORS

**Application:** Process Payment Items for Invoices

**Example:** Generate payment run for all CN13 vendors due by week end

**Steps:**
1. Open **Process Payment Items for Invoices**
2. Enter selection:
   - Company Code: **CN13**
   - Vendor: Leave blank (all vendors)
   - Payment Date: **2025-01-31** (when payment should post)
   - Due Date: **2025-01-31** (pay items due by this date)
   - House Bank: **CN13BK01** (China bank account)

3. Click "Generate Proposal"
4. System displays proposal list with all invoices to pay

5. Review proposal:
   - Check amounts look correct
   - Check payment methods (usually D or I)
   - Review exception list for any blocked items
   - Remove any items you don't want to pay yet

6. Click "Execute Payment Run"
7. System posts payments and creates payment documents
8. Click "Download Payment File"
9. Save file as: **Payment_CN13_20250131.xml**
10. Upload file to bank's online portal
11. Submit for approval in bank system

**Home Control House Banks:**
- SG21BK01 = DBS Bank Singapore
- CN13BK01 = ICBC Suzhou
- CN17BK01 = Bank of China Shanghai
- BE10BK01 = KBC Belgium

---

### 6. HANDLE PAYMENT EXCEPTION

**Example:** Vendor 1000789 appears in exception list "Bank details missing"

**Steps:**
1. Note vendor number and reason from exception list
2. Open **Manage Supplier Master Data**
3. Search for vendor **1000789**
4. Click "Change"
5. Go to Company Code Data → Payment Transactions tab
6. Enter missing bank information:
   - Bank Country: **CN**
   - Bank Key: **102584000123** (bank code)
   - Account Number: Vendor's account number
   - Account Holder: Vendor's legal name
   - SWIFT Code: If international payment
7. Save
8. Return to payment run and regenerate proposal
9. Vendor should now appear in payment list

---

## ACCOUNTS RECEIVABLE PROCEDURES

### 7. POST CUSTOMER PAYMENT

**Application:** Post Incoming Payments

**Example:** Customer 2000345 paid invoice via bank transfer, $15,000 received

**Steps:**
1. Open **Post Incoming Payments**
2. Enter:
   - Company Code: **SG21**
   - Customer: **2000345**
   - Amount: **15000.00**
   - Currency: **SGD**
   - Payment Date: Date received in bank (from bank statement)
   - House Bank: **SG21BK01**
   - Reference: Bank transfer reference or check number

3. Click "Process Open Items"
4. System shows customer's open invoices:
   ```
   Invoice 9000123456  $10,000  Due: 2025-01-15
   Invoice 9000123789  $5,000   Due: 2025-01-20
   ```

5. Select invoices to clear (system proposes automatic clearing):
   - Check both invoices (totaling $15,000)
   - System matches payment to invoices

6. Click "Post"
7. System clears both invoices
8. Customer AR balance reduced by $15,000

**If partial payment received:**
- Select invoice(s) totaling closest to payment amount
- Post partial payment against largest invoice
- Residual item remains open for balance

---

### 8. PROCESS CUSTOMER PAYMENT WITH DISCOUNT

**Example:** Customer paid $9,800 for $10,000 invoice (took 2% early payment discount)

**Steps:**
1. Open **Post Incoming Payments**
2. Enter payment amount received: **9800.00**
3. Select invoice: **$10,000** due
4. System calculates:
   - Invoice amount: 10,000
   - Payment received: 9,800
   - Discount taken: 200
5. Check if discount is within terms (2/10 Net 30 means 2% if paid in 10 days)
6. If within terms, system automatically accounts for cash discount
7. Post payment
8. Invoice fully cleared, discount posted to expense account

---

## FIXED ASSETS PROCEDURES

### 9. CREATE ASSET MASTER

**Application:** Manage Asset Master Data

**Example:** New laser cutting machine purchased for CN13 factory, cost $120,000

**Steps:**
1. Open **Manage Asset Master Data** → Click "Create"
2. Enter:
   - Company Code: **CN13**
   - Asset Class: **ZH300000** (Machinery & Installations)
   - Description: "Laser Cutting Machine - Model XYZ-2000"

3. General Data:
   - Cost Center: **CN13MF1** (Manufacturing Suzhou)
   - Location: "Factory Building A, Floor 2"
   - Serial Number: (from equipment nameplate)
   - Manufacturer: Equipment supplier name

4. Depreciation:
   - Useful Life: **10** years (per company policy for machinery)
   - Depreciation Key: **LINA** (straight-line)
   - Depreciation Start Date: Date machine ready for use (not purchase date!)
   - Scrap Value: Usually 0

5. Save → Note asset number (e.g., **000030012345**)

**Common Asset Classes at Home Control:**
- ZH300000 = Machinery & Equipment
- ZH450300 = IT Equipment
- ZH450410 = Office Furniture
- ZH102000 = Buildings

**Useful Life Guidelines:**
- Machinery: 10 years
- IT Equipment: 3-5 years
- Office Furniture: 5 years
- Vehicles: 5 years

---

### 10. CAPITALIZE ASSET FROM PURCHASE ORDER

**Example:** Asset 000030012345 (machine) received from PO 4500678901

**Scenario:** When you receive the machine and post goods receipt against PO that references asset number, system automatically capitalizes the asset.

**Steps:**
1. Verify asset master created (see procedure 9)
2. When warehouse posts goods receipt from PO:
   - System reads asset number from PO
   - Automatically posts to asset
   - Asset value increases by invoice amount
3. Check asset value:
   - Open **Display Asset Explorer**
   - Enter asset number: **000030012345**
   - Verify acquisition value shows: **$120,000**
   - Verify status: Capitalized

**You don't need to post separately - GR against PO with asset reference does it automatically!**

---

## CONTROLLING PROCEDURES

### 11. CREATE COST CENTER

**Application:** Manage Cost Centers

**Example:** New R&D team in Singapore needs cost center

**Steps:**
1. Get approval from Finance Manager
2. Open **Manage Cost Centers** → Click "Create"
3. Enter:
   - Controlling Area: **HC01** (Home Control)
   - Cost Center ID: **SG21RD2** (follow naming convention)
   - Valid From: Start date (e.g., 2025-02-01)
   - Valid To: Usually 9999-12-31 (indefinite)

4. Master Data:
   - Name: "R&D Team 2 Singapore"
   - Description: "Product Development - Smart Home Devices"
   - Department: R&D
   - Company Code: **SG21**
   - Profit Center: **PC-SG21** (Singapore profit center)
   - Cost Center Category: **A** (Revenue producing)
   - Person Responsible: Manager's name

5. Save cost center number
6. Update cost center in hierarchy:
   - Open **Manage Global Hierarchies**
   - Type: Cost Center Hierarchy
   - Hierarchy: **HC01** (standard hierarchy)
   - Add new cost center under SG21 → R&D branch

7. Inform requester cost center is ready

**Cost Center Naming Convention:**
- Format: [CompanyCode][Function][Number]
- SG21MF1 = Singapore Manufacturing 1
- CN13QC1 = Suzhou Quality Control 1
- SG21RD2 = Singapore R&D 2

---

### 12. POST TO COST CENTER (via Journal Entry)

**Example:** Allocate shared IT costs to multiple cost centers

**Steps:**
1. Open **Manage Journal Entries**
2. Create debit lines for each receiving cost center:
   ```
   Debit: GL 62001 (IT Expense), CC: SG21MF1, $5,000
   Debit: GL 62001 (IT Expense), CC: SG21SA1, $3,000
   Debit: GL 62001 (IT Expense), CC: SG21FI1, $2,000
   Credit: GL 62099 (IT Allocation Pool), $10,000
   ```
3. Post
4. Each cost center now shows their share of IT expense

---

## PRACTICAL SCENARIOS

### Scenario A: Month-End Closing for CN13

**Date: February 1, 2025 (Close January)**

**Your role: GL Processing Officer**

1. **9:00 AM** - Check parked documents:
   - 2 parked journals found from last week
   - Review and post them to January

2. **10:00 AM** - Post accruals:
   - Utilities accrual: $8,500 (not yet invoiced)
   - Salary accrual: $45,000 (payroll runs Feb 5)

3. **11:00 AM** - Review exception report:
   - Found GL account 68523 with suspicious large amount
   - Investigate: was supposed to be 68233
   - Post correction journal

4. **2:00 PM** - Run preliminary reports:
   - P&L looks reasonable
   - Balance sheet balances
   - No large unexpected variances

5. **4:00 PM** - Email GL Executive Periodic:
   - "CN13 January ready for close"
   - Attach preliminary financials

---

### Scenario B: Urgent Payment Request

**Situation:** Supplier 1000456 calls - their invoice wasn't paid, they're holding shipment

**Your role: AP Processing Officer**

1. **Step 1:** Look up supplier in SAP
   - Open **Supplier Line Items**
   - Enter vendor: 1000456, Company: CN13
   - Check open items

2. **Step 2:** Found invoice 5100678901 for $15,000, due yesterday
   - Status: Open (not paid)
   - Payment block: Yes (block reason: "Missing approval")

3. **Step 3:** Check why blocked
   - Call purchasing - they confirm goods received OK
   - Call finance manager - she approves payment

4. **Step 4:** Remove block
   - Open invoice in change mode
   - Remove payment block
   - Save

5. **Step 5:** Make emergency payment
   - Run payment proposal for this vendor only
   - Process immediately
   - Download payment file
   - Upload to bank (same day value if before cutoff)
   - Confirm with supplier payment sent

---

### Scenario C: Customer Disputes Invoice Amount

**Situation:** Customer 2000567 says invoice 9000345678 should be $9,500 not $10,000

**Your role: AR Processing Officer**

1. **Step 1:** Display invoice
   - Open **Manage Billing Documents**
   - Enter invoice 9000345678
   - Review: Invoice shows $10,000 for 1,000 units @ $10/unit

2. **Step 2:** Check sales order
   - Click document flow to see sales order
   - Sales order shows: 1,000 units @ $9.50/unit = $9,500
   - **Issue found:** Billing used wrong price!

3. **Step 3:** Create credit memo
   - Can't change posted invoice
   - Create credit memo for $500 difference
   - Reference original invoice
   - Post credit memo

4. **Step 4:** Inform customer
   - Email: "Credit memo CM-9000567890 for $500 issued"
   - Net amount due: $9,500 ($10,000 invoice - $500 credit)

---

## QUICK REFERENCE

### Company Codes
- **SG21** = Singapore (HQ)
- **CN13** = Suzhou factory
- **CN17** = Shanghai office
- **BE10** = Belgium
- **US10** = USA

### Currencies
- SG21 = SGD
- CN13/CN17 = CNY
- BE10 = EUR
- US10 = USD

### Tax Codes
**Singapore:**
- P9 = 9% purchase tax
- S9 = 9% sales tax
- P0/S0 = 0% tax

**China:**
- J2 = 13% input tax
- X2 = 13% output tax
- J0/X0 = 0% tax

### Payment Terms
- Z000 = Due immediately
- Z030 = Net 30 days
- Z045 = Net 45 days
- Z210 = 2% discount if paid in 10 days, net 30

### Key Contacts
- GL questions: Sally Jin (sally.jin@homecontrol.com)
- AP questions: Nicole Li (nicole.li@homecontrol.com)
- System issues: IT Helpdesk (ext. 8888)

---

*End of Finance Procedures*

