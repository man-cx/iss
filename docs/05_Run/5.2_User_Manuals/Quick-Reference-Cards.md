# SAP S/4HANA Quick Reference Cards
## Home Control - End-User Training

---

## Purpose

This document provides one-page quick reference guides for the most frequently performed processes in SAP. Print these cards and keep them at your desk for easy reference.

---

## TABLE OF CONTENTS

**Finance Department:**
1. Create GL Journal Entry
2. Post Vendor Invoice
3. Process Vendor Payment
4. Post Customer Payment
5. Create Asset Master

**Purchasing & MM Department:**
6. Create Material Master
7. Create Supplier Master
8. Create Purchase Order
9. Run MRP

**Warehouse Department:**
10. Post Goods Receipt from PO
11. Post Goods Issue to Production
12. Perform Physical Inventory Count

**Sales Department:**
13. Create Customer Master
14. Create Sales Order
15. Create Outbound Delivery
16. Create Billing Document

**Production Planning Department:**
17. Create Bill of Material (BOM)
18. Run Material Requirements Planning
19. Create Production Order
20. Confirm Production Order

---

## FINANCE DEPARTMENT QUICK REFERENCE CARDS

### 1. CREATE GL JOURNAL ENTRY

**Application:** Manage Journal Entries

**When to Use:** Manual GL postings, accruals, adjustments, reclassifications

**Quick Steps:**
1. Open **Manage Journal Entries**
2. Click "Create"
3. Enter header:
   - Company Code
   - Posting Date
   - Document Date
   - Reference
   - Description
4. Enter debit line(s):
   - GL Account
   - Amount
   - Cost Center (if expense)
   - Text
5. Enter credit line(s):
   - GL Account
   - Amount
   - Text
6. Verify debits = credits (Balance = 0)
7. Click "Check" (✓)
8. Click "Post"
9. Save document number

**Key Fields:**
- **Posting Date**: Determines which period affected
- **GL Account**: Account to post to
- **Amount**: Positive for both debit and credit
- **Cost Center**: Required for expense accounts

**Tips:**
- Always use Check before Post
- Save document number for audit trail
- Use clear descriptions
- Verify balance = 0

---

### 2. POST VENDOR INVOICE

**Application:** Create Incoming Invoices

**When to Use:** Vendor invoices without purchase orders

**Quick Steps:**
1. Open **Create Incoming Invoices**
2. Enter header:
   - Company Code
   - Vendor Number
   - Invoice Date
   - Posting Date
   - Invoice Amount
   - Reference (vendor invoice number)
3. Enter line items:
   - GL Account (expense account)
   - Amount
   - Cost Center
   - Text
4. System calculates vendor payable line
5. Click "Check"
6. Click "Post"
7. Save document number

**Key Fields:**
- **Vendor**: Supplier to be paid
- **Invoice Date**: Date on vendor invoice
- **Reference**: Vendor invoice number (important!)
- **GL Account**: Expense account

**Tips:**
- Enter vendor invoice number in Reference field
- Verify total matches vendor invoice
- Check payment terms correct
- Attach scan of invoice for audit

---

### 3. PROCESS VENDOR PAYMENT

**Application:** Process Payment Items for Invoices

**When to Use:** Pay approved vendor invoices

**Quick Steps:**
1. Open **Process Payment Items for Invoices**
2. Enter selection criteria:
   - Company Code
   - Vendor (or leave blank for all)
   - Due date range
3. Click "Generate Proposal"
4. Review proposal list
5. Remove any items not to be paid
6. Verify payment methods and amounts
7. Click "Execute Payment Run"
8. System posts payments
9. Download payment file
10. Upload to bank portal

**Key Information:**
- **Payment Proposal**: List of invoices to pay
- **Due Date**: When payment should be made
- **Payment Method**: Bank transfer, check, etc.

**Tips:**
- Review exception list carefully
- Check bank balances before processing
- Download payment file immediately
- Verify file uploaded successfully to bank

---

### 4. POST CUSTOMER PAYMENT

**Application:** Post Incoming Payments

**When to Use:** Record customer payments received

**Quick Steps:**
1. Open **Post Incoming Payments**
2. Enter:
   - Company Code
   - Customer Number
   - Payment Amount
   - Payment Date
   - Bank Account (house bank)
   - Reference (check number, transfer reference)
3. Click "Process Open Items"
4. System displays open invoices
5. Select invoices to clear with payment
6. System proposes clearing
7. Verify amount matches
8. Click "Post"
9. Payment posted, invoices cleared

**Key Fields:**
- **Customer**: Who paid
- **Amount**: Payment received
- **Reference**: Check number or bank reference
- **Open Items**: Invoices to clear

**Tips:**
- Match payment to specific invoices when possible
- Use automatic clearing for efficiency
- Handle partial payments carefully
- Document any payment discrepancies

---

### 5. CREATE ASSET MASTER

**Application:** Manage Asset Master Data

**When to Use:** Acquire new fixed assets

**Quick Steps:**
1. Open **Manage Asset Master Data**
2. Click "Create"
3. Enter:
   - Company Code
   - Asset Class (determines number range and accounts)
   - Description (clear asset name)
4. Enter master data:
   - Cost Center (where asset located)
   - Business Area/Profit Center
   - Asset Location
5. Enter depreciation data:
   - Useful Life (years)
   - Depreciation Key
   - Depreciation Start Date
6. Save asset number
7. Asset ready for acquisition posting

**Key Fields:**
- **Asset Class**: Type of asset (building, equipment, vehicle, etc.)
- **Description**: Clear identification of asset
- **Cost Center**: Where asset is used
- **Useful Life**: How many years it will depreciate
- **Depr. Key**: Depreciation method (straight-line, declining, etc.)

**Tips:**
- Use descriptive names (not "Asset 123")
- Verify cost center assignment
- Check useful life against policy
- Save asset number for PO reference

---

## PURCHASING & MM DEPARTMENT QUICK REFERENCE CARDS

### 6. CREATE MATERIAL MASTER

**Application:** Manage Product Master Data

**When to Use:** Create new material (finished goods, raw materials, components)

**Quick Steps:**
1. Get material number from Smart-Fulfillment (FG) or internal assignment (RM)
2. Open **Manage Product Master Data**
3. Click "Create" or search for material if auto-created
4. Enter Basic Data:
   - Material Number
   - Material Type (FERT, ROH, HALB)
   - Description (English and Chinese)
   - Base Unit (EA, KG, M)
   - Material Group
5. Enter MRP Data:
   - MRP Type: PD
   - Procurement Type: E (make) or F (buy)
   - Lot Size
   - Safety Stock
   - Lead Time
6. Enter Purchasing Data:
   - Purchasing Group
   - Plant
7. Enter Accounting Data:
   - Valuation Class
   - Price Control
8. If sold, enter Sales Data
9. Change status to ZD (Released) after costing
10. Save

**Material Status Codes:**
- ZA: Created (not usable)
- ZB: Pending Purchasing
- ZC: Pending Costing
- ZD: Released (active - use this!)

**Tips:**
- Always search first to avoid duplicates
- Use clear descriptions
- Complete all required views before releasing
- Verify material status = ZD before use

---

### 7. CREATE SUPPLIER MASTER

**Application:** Manage Supplier Master Data

**When to Use:** Add new vendor/supplier

**Quick Steps:**
1. Collect supplier information (name, address, bank details)
2. Obtain approvals (AP, Finance, Purchasing)
3. Open **Manage Supplier Master Data**
4. Click "Create"
5. Select supplier group (Z001 = regular supplier)
6. Enter General Data:
   - Name
   - Address
   - Contact info
7. Enter Company Code Data:
   - Reconciliation Account
   - Payment Terms
   - Bank Details (account number, SWIFT code)
8. Enter Purchasing Organization Data:
   - Purchasing Group
   - Currency
9. Save supplier number
10. Test by creating PO

**Supplier Groups:**
- Z001: Regular suppliers (BOM/NPR)
- Z002: Intercompany
- ZEMP: Employees
- ZCPD: One-time vendors

**Tips:**
- Verify bank details carefully (payment errors are costly!)
- Use legal entity name
- Double-check SWIFT codes
- Keep original documents for audit

---

### 8. CREATE PURCHASE ORDER

**Application:** Create Purchase Order

**When to Use:** Order materials from suppliers

**Quick Steps:**
1. Open **Create Purchase Order**
2. Enter header:
   - Vendor Number
   - Company Code
   - Purchasing Organization
   - Purchasing Group
3. For each line item:
   - Material Number
   - Quantity
   - Delivery Date
   - Plant
   - Storage Location
4. System fills:
   - Price (from info record)
   - Delivery time
5. Review pricing
6. Add delivery address if needed
7. Add texts/special instructions
8. Click "Save"
9. Note PO number
10. Send PO to supplier (print or email)

**Key Fields:**
- **Vendor**: Who to buy from
- **Material**: What to buy
- **Quantity**: How much
- **Delivery Date**: When needed
- **Price**: Cost per unit

**Tips:**
- Use info records for automatic pricing
- Verify delivery dates realistic
- Enter clear delivery instructions
- Send PO to supplier promptly
- Follow up on confirmations

---

### 9. RUN MRP

**Application:** Single-Item MRP / Collective MRP Run

**When to Use:** Calculate material requirements and create procurement proposals

**Quick Steps:**
1. Open **Collective MRP Run** (or Single-Item for one material)
2. Enter:
   - Plant
   - Processing Key: NETCH (net change)
   - Planning Mode: 1 (create procurement elements)
3. Click "Execute"
4. Wait for completion
5. Open **Evaluating MRP Results** or **Display Stock/Requirements List**
6. Review planned orders and PRs created
7. Check for exception messages
8. Process exceptions:
   - Reschedule
   - Cancel
   - Quantity changes
9. Convert planned orders to production orders
10. Monitor PRs conversion by Purchasing

**MRP Creates:**
- **Planned Orders**: For materials to produce (make)
- **Purchase Requisitions**: For materials to buy (buy)
- **Exception Messages**: Problems to resolve

**Tips:**
- Run MRP daily at consistent time
- Process exceptions immediately
- Don't ignore exception messages!
- Coordinate with Purchasing on critical PRs
- Keep master data current for accurate results

---

## WAREHOUSE DEPARTMENT QUICK REFERENCE CARDS

### 10. POST GOODS RECEIPT FROM PO

**Application:** Post Goods Receipt

**When to Use:** Receive materials from supplier

**Quick Steps:**
1. Receive physical delivery from supplier
2. Open **Post Goods Receipt**
3. Enter PO number
4. System displays PO line items
5. For each item being received:
   - Enter GR Quantity
   - Verify/select Storage Location
   - Enter Batch (if applicable)
6. Enter Delivery Note number (from packing slip)
7. Click "Check"
8. Click "Post"
9. Note Material Document Number
10. Print GR label
11. Attach label to materials
12. Put away to storage location

**Key Fields:**
- **PO Number**: From supplier's packing slip
- **GR Quantity**: What you physically counted
- **Storage Location**: Where material will be stored
- **Delivery Note**: Supplier's packing slip number

**Tips:**
- Always count physically - don't trust packing slip
- Only post what you have in hand
- Print labels immediately
- Put away promptly to correct location
- Save material document number

---

### 11. POST GOODS ISSUE TO PRODUCTION

**Application:** Post Goods Issue / Goods Issue for Order

**When to Use:** Issue components to production order

**Quick Steps:**
1. Receive material request from production
2. Open **Goods Issue for Order**
3. Enter Production Order Number
4. System displays required components
5. Pick materials from storage
6. In SAP, verify:
   - Materials correct
   - Quantities correct
   - Storage locations correct
7. Click "Post"
8. Material Document created
9. Inventory reduced
10. Production order debited

**Key Fields:**
- **Production Order**: Order consuming materials
- **Material**: Component being issued
- **Quantity**: Amount issued
- **Storage Location**: Where picked from

**Tips:**
- Verify production order number with production supervisor
- Issue full quantity when possible
- Note any shortages immediately
- Update production if materials not available
- Keep shop floor informed

---

### 12. PERFORM PHYSICAL INVENTORY COUNT

**Applications:** Create Physical Inventory Document, Enter Physical Inventory Count, Post Physical Inventory Difference

**When to Use:** Scheduled inventory count (monthly, quarterly, annually)

**Quick Steps:**
1. **Create PI Document**:
   - Open **Create Physical Inventory Document**
   - Select Plant, Storage Location
   - Select materials to count (all or selected)
   - Enter count date
   - Create document, note PI number
2. **Print Count Sheets**:
   - Print count sheets (without book quantities for blind count)
   - Distribute to count team
3. **Physical Count**:
   - Count all materials systematically
   - Record on count sheets
   - Mark "NOT FOUND" if missing
   - Sign count sheets
4. **Enter Counts**:
   - Open **Enter Physical Inventory Count**
   - Enter PI document number
   - Enter counted quantities from sheets
   - System shows differences
5. **Investigate Differences**:
   - Recount significant variances
   - Research causes
   - Document findings
   - Get approvals for large differences
6. **Post Differences**:
   - Open **Post Physical Inventory Difference**
   - Review all differences
   - Click "Post"
   - System updates inventory to match count

**Key Concepts:**
- **Book Quantity**: What SAP shows
- **Counted Quantity**: What you physically counted
- **Difference**: Counted - Book
- **Positive Diff**: Found more (gain)
- **Negative Diff**: Found less (loss)

**Tips:**
- Blind counts are more accurate
- Two-person teams reduce errors
- Recount high-value items
- Investigate large differences before posting
- Document everything for audit

---

## SALES DEPARTMENT QUICK REFERENCE CARDS

### 13. CREATE CUSTOMER MASTER

**Application:** Manage Customer Master Data

**When to Use:** Add new customer

**Quick Steps:**
1. Collect customer information and credit approval
2. Open **Manage Customer Master Data**
3. Click "Create"
4. Select account group (Z001 = standard customer)
5. Enter General Data:
   - Name (legal entity)
   - Address
   - Contact info
6. Enter Company Code Data:
   - Reconciliation Account
   - Payment Terms
   - Currency
7. Enter Sales Area Data:
   - Sales Org, Distribution Channel, Division
   - Customer Group
   - Pricing Procedure
   - Incoterms
   - Shipping Conditions
8. Set Credit Limit (Credit Controller)
9. Save customer number
10. Test by creating sales order

**Key Fields:**
- **Name**: Legal entity name
- **Payment Terms**: When invoices due (Net 30, etc.)
- **Credit Limit**: Maximum exposure
- **Pricing Procedure**: Which discounts apply
- **Incoterms**: Ownership transfer point (FOB, CIF, etc.)

**Tips:**
- Get credit approval before creating
- Use legal names, not nicknames
- Verify tax classification
- Create ship-to addresses for multiple locations
- Test with sample order

---

### 14. CREATE SALES ORDER

**Application:** Create Sales Order

**When to Use:** Customer places order

**Quick Steps:**
1. Receive customer PO
2. Open **Create Sales Order**
3. Select order type (OR = standard)
4. Enter header:
   - Sold-to Party (customer number)
   - Ship-to Party (if different)
   - Customer PO Number (required!)
   - PO Date
   - Requested Delivery Date
5. Add line items:
   - Material Number
   - Order Quantity
   - Unit
6. System performs:
   - ATP check (availability)
   - Pricing
   - Credit check
7. Review:
   - Confirmed quantities and dates
   - Prices
   - Credit status
8. Add delivery instructions in texts
9. Click "Save"
10. Note Sales Order Number
11. Print and send Order Confirmation to customer

**Key Information:**
- **Green ATP**: Stock available
- **Yellow ATP**: Partial availability
- **Red ATP**: Not available
- **Credit OK**: Can proceed
- **Credit Block**: Need approval

**Tips:**
- Always enter customer PO number!
- Check ATP before promising delivery
- Verify pricing matches agreement
- Send order confirmation same day
- If credit blocked, contact Credit Controller immediately

---

### 15. CREATE OUTBOUND DELIVERY

**Application:** Create Outbound Delivery

**When to Use:** Create delivery for sales order ready to ship

**Quick Steps:**
1. Open **Create Outbound Delivery**
2. Search for due orders:
   - By sales order number
   - By customer
   - By delivery date range
3. Select order(s) to deliver
4. Click "Create Delivery"
5. System creates delivery with:
   - Materials from order
   - Quantities
   - Ship-to address
6. Verify quantities
7. Save delivery number
8. Print picking list
9. Warehouse picks materials
10. Pack goods
11. Post Goods Issue (PGI)
12. Print delivery note
13. Ship to customer

**Key Fields:**
- **Sales Order**: Source order
- **Delivery Number**: Delivery document number
- **Picking Status**: Not picked / Picked / Shipped
- **GI Status**: Not done / Done

**Tips:**
- Create deliveries for orders ready to ship (stock available)
- Print pick lists immediately
- Coordinate with warehouse
- Post GI same day as shipment
- Verify ship-to address before sending

---

### 16. CREATE BILLING DOCUMENT

**Application:** Create Billing Document / Manage Billing Documents

**When to Use:** Invoice customer after delivery

**Quick Steps:**
1. Delivery completed with Goods Issue posted
2. Open **Create Billing Document**
3. Select deliveries to bill:
   - By delivery number
   - By customer
   - By billing date range
4. Click "Create Billing"
5. System creates invoice with:
   - Materials delivered
   - Quantities
   - Prices from order
   - Taxes
6. Review billing document
7. System posts to accounting (creates AR invoice)
8. Print invoice
9. Send to customer (email or mail)
10. For China: Create Golden Tax Invoice

**Key Information:**
- **Billing Document**: Invoice number
- **Billing Date**: Invoice date
- **Amount**: Total invoice value
- **Due Date**: When payment expected

**Tips:**
- Bill promptly after delivery (same day)
- Review billing list daily
- Verify prices match orders
- Send invoices immediately
- Monitor payments in AR

---

## PRODUCTION PLANNING DEPARTMENT QUICK REFERENCE CARDS

### 17. CREATE BILL OF MATERIAL (BOM)

**Application:** Maintain Bill of Material

**When to Use:** Create BOM for new product or change existing

**Quick Steps:**
1. Collect component list from R&D
2. Verify all component materials exist in SAP
3. Open **Maintain Bill of Material**
4. Click "Create"
5. Enter:
   - Material (finished good)
   - Plant
   - BOM Usage: 1 (Production)
   - Valid From date
   - Base Quantity: 1
6. Add components:
   - Item Number (10, 20, 30...)
   - Component Material
   - Quantity per FG
   - Unit
   - Scrap %
7. Repeat for all components
8. Set BOM Status = 4 (Active) when ready
9. Save BOM

**Key Fields:**
- **Material**: Finished good this BOM is for
- **Component**: Material consumed
- **Quantity**: How many per finished good
- **Scrap %**: Waste allowance
- **BOM Status**: 1=Development, 4=Active

**Tips:**
- Verify all components exist first
- Double-check quantities
- Use scrap % for high-waste items
- Don't release until verified by R&D and Production
- Update promptly when engineering changes

---

### 18. RUN MATERIAL REQUIREMENTS PLANNING

**Application:** Collective MRP Run

**When to Use:** Calculate production and procurement requirements

**Quick Steps:**
1. Open **Collective MRP Run**
2. Enter:
   - Plant
   - Processing Key: NETCH
   - Planning Mode: 1
3. Click "Execute"
4. MRP calculates:
   - Net requirements
   - Creates planned orders (production)
   - Creates PRs (purchasing)
   - Generates exceptions
5. Review results in **Display Stock/Requirements List**
6. Process exception messages
7. Convert planned orders to production orders
8. Monitor PR conversion by Purchasing

**What MRP Does:**
- Reads demand (sales orders, forecasts)
- Checks stock
- Checks receipts (POs, orders)
- Calculates needs
- Creates procurement proposals

**Tips:**
- Run daily at same time
- Process exceptions immediately
- Don't ignore warnings!
- Keep master data current
- Coordinate with Purchasing on critical items

---

### 19. CREATE PRODUCTION ORDER

**Application:** Create Production Order

**When to Use:** Convert planned order to firm order or create manually

**Quick Steps:**
1. Open **Create Production Order**
2. Enter:
   - Material (what to produce)
   - Order Quantity
   - Production Plant
3. System automatically:
   - Explodes BOM (lists components)
   - Copies routing (operations)
   - Schedules dates
4. Review:
   - Start date
   - Finish date
   - Components
   - Material availability
5. Click "Save"
6. Note Production Order Number
7. Release order when ready to start

**Key Information:**
- **Planned Order**: MRP proposal (not firm)
- **Production Order**: Firm order (reserves materials)
- **Released**: Ready for shop floor
- **Confirmed**: Production reported

**Tips:**
- Check component availability before release
- Review dates are realistic
- Print shop papers after release
- Release in sequence needed
- Don't release too early (ties up materials)

---

### 20. CONFIRM PRODUCTION ORDER

**Application:** Confirm Production Order

**When to Use:** Record production output

**Quick Steps:**
1. Production completes manufacturing
2. Open **Confirm Production Order**
3. Enter Production Order Number
4. Enter:
   - Operation Number (if multi-operation)
   - Yield Quantity (good output)
   - Scrap Quantity (rejected)
   - Actual Hours worked
   - Confirmation Date
5. Click "Post"
6. System automatically:
   - Posts goods receipt for finished goods
   - Relieves (consumes) components
   - Records labor time
   - Calculates variances
7. Save confirmation number
8. Finished goods now in inventory

**Key Fields:**
- **Production Order**: Which order
- **Yield Qty**: Good output produced
- **Scrap Qty**: Rejected/scrapped
- **Actual Hours**: Time worked

**Tips:**
- Confirm same day as production
- Enter accurate scrap quantities
- Record actual time for costing accuracy
- If components short, issue manually first
- Check finished goods received in inventory

---

## GENERAL TIPS FOR ALL USERS

### Navigation
- Use `Enter` key to move between fields
- Use `F3` to go back
- Use `Ctrl + S` to save
- Bookmark favorite applications

### Data Entry
- Always use **Check** function before **Post**
- Save document numbers immediately
- Enter clear descriptions
- Verify dates carefully

### Problem Solving
- If error occurs, read message carefully
- Use Help icon (?) for field explanations
- Don't click randomly - ask for help
- Document unusual situations

### Best Practices
- Process transactions promptly
- Keep master data current
- File supporting documents
- Follow approval processes
- Review work before posting

---

## CONTACTS FOR HELP

**IT Help Desk:**
- Email: helpdesk@homecontrol.com
- Phone: +XX-XXXX-XXXX
- For: Login issues, system errors, technical problems

**Department Contacts:**
- Finance Manager: [Contact]
- Purchasing Manager: [Contact]
- Warehouse Supervisor: [Contact]
- Sales Manager: [Contact]
- Production Planning Manager: [Contact]

**Training Resources:**
- Detailed training manuals: [Location]
- Video tutorials: [URL]
- SAP Learning Portal: [URL]

---

## DOCUMENT INFORMATION

**Version:** 1.0  
**Date:** January 2025  
**Prepared by:** Training Development Team  
**Updates:** Contact Training Department for updates or corrections

---

*Print individual cards and laminate for desk reference!*

