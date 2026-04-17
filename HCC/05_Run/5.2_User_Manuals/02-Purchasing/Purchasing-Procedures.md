# Purchasing & Materials Management - SAP Procedures
## Home Control SAP S/4HANA

---

## MATERIAL MASTER PROCEDURES

### 1. CREATE FINISHED GOODS MATERIAL

**Application:** Manage Product Master Data

**Example:** New remote control model RC-3000 designed by R&D

**Steps:**
1. R&D logs into Smart-Fulfillment System
2. Applies for material number → Gets **RC-3000-BK** (Black version)
3. Smart-Fulfillment creates material in SAP automatically
4. Material Status = **ZA** (Created, not usable yet)

5. You (Master Data Team) complete the material:
   - Open **Manage Product Master Data**
   - Search: **RC-3000-BK**
   - Click "Change"

6. **MRP View:**
   - MRP Type: **PD**
   - Procurement Type: **E** (make in-house)
   - Lot Size: **EX** (Lot-for-lot)
   - Safety Stock: **500** units
   - Planned Delivery Time: **15** days (production lead time)
   - MRP Controller: **001** (your ID)

7. **Purchasing View:**
   - Purchasing Group: **P01** (Production Materials)
   - Plant: **CN13** (Suzhou)
   - Over-delivery: **5.0%**
   - Under-delivery: **2.0%**

8. **Finance View:**
   - Valuation Class: **7920** (FG Trading Goods)
   - Price Control: **S** (Standard price)
   - Price Unit: **1**

9. **Sales View:**
   - Sales Org: **CN13** / Distribution Channel: **10** / Division: **00**
   - Item Category Group: **NORM**
   - Availability Check: **02** (ATP check)

10. Change Status: **ZA** → **ZB** (Pending Purchasing)
11. After Finance runs costing: **ZB** → **ZD** (Released)
12. Save

**Material Status Flow:**
- ZA (Created) → ZB (Pending Purchasing) → ZC (Pending Costing) → **ZD (Released - Ready to Use)**

---

### 2. CREATE RAW MATERIAL (Component)

**Example:** New PCB board component for RC-3000

**Steps:**
1. R&D requests in Smart-Fulfillment → Gets **PCB-RC3000-MAIN**
2. R&D sets basic data, Status = **ZA**

3. You (Purchasing) complete:
   - Open material **PCB-RC3000-MAIN** in change mode

4. **MRP View:**
   - MRP Type: **PD**
   - Procurement Type: **F** (buy from supplier)
   - Lot Size: **FX** (Fixed lot: 1000 units)
   - Safety Stock: **200** units
   - Planned Delivery Time: **30** days (supplier lead time)

5. **Purchasing View:**
   - Purchasing Group: **P02** (Electronic Components)
   - Plant: **CN13**
   - Standard Price: **$2.50** (current supplier quote)
   - Order Unit: **EA**

6. Status: **ZA** → **ZB**
7. Create info record with supplier (see procedure 4)
8. Status: **ZB** → **ZC**
9. Finance runs costing
10. Status: **ZC** → **ZD**

**Common Material Types:**
- **FERT** = Finished Goods (RC-3000, RC-2000)
- **ROH** = Raw Materials (PCB boards, plastic housing)
- **HALB** = Semi-Finished (sub-assemblies)

---

## SUPPLIER MASTER PROCEDURES

### 3. CREATE SUPPLIER

**Application:** Manage Supplier Master Data

**Example:** New PCB supplier in Shenzhen - Shenzhen Tech Components Ltd.

**Steps:**
1. Get completed Supplier Information Form from Commodity Manager
2. AP Admin validates bank details
3. Get approvals (Finance Controller, Purchasing Director)

4. Open **Manage Supplier Master Data** → Click "Create"
5. Supplier Group: **Z001** (Regular BOM vendor)
6. System assigns number: **1002345**

7. **General Data:**
   - Name: "Shenzhen Tech Components Ltd."
   - Search Term: "SZTECH"
   - Street: 25 Huaqiang North Road
   - City: Shenzhen
   - Postal Code: 518000
   - Country: **CN**
   - Region: 44 (Guangdong)
   - Phone: +86-755-8888-9999
   - Email: sales@sztechcomponents.com

8. **Company Code Data (CN13):**
   - Reconciliation Account: **210000** (AP Control)
   - Payment Terms: **Z045** (Net 45 days)
   - Payment Methods: **D** (Domestic transfer)
   - Bank Country: **CN**
   - Bank Key: **102584001234**
   - Account Number: 62218801234567890
   - Account Holder: "Shenzhen Tech Components Ltd."

9. **Purchasing Org Data (CN13):**
   - Purchasing Group: **P02**
   - Currency: **CNY**
   - Terms of Payment: **Z045**
   - GR-Based Invoice Verification: ✓ (Check - auto-create invoice on GR)

10. Save → Supplier **1002345** ready
11. Email Commodity Manager: "Supplier 1002345 created and ready for POs"

**Supplier Groups:**
- Z001 = Regular suppliers (7-digit number)
- Z002 = Intercompany (4-digit)
- ZEMP = Employees

---

## PURCHASING INFO RECORD PROCEDURES

### 4. CREATE INFO RECORD WITH PRICE

**Application:** Manage Purchasing Info Records

**Example:** PCB board PCB-RC3000-MAIN from supplier 1002345 at $2.35/pc

**Steps:**
1. Get PPCA Form (Price & Purchase Condition Agreement) from buyer:
   - Material: PCB-RC3000-MAIN
   - Supplier: 1002345 (Shenzhen Tech)
   - Price: $2.35/pc
   - Valid from: 2025-02-01
   - MOQ: 1,000 pcs
   - Lead time: 30 days

2. Open **Create Info Record**
3. Enter:
   - Supplier: **1002345**
   - Material: **PCB-RC3000-MAIN**
   - Purchasing Org: **CN13**
   - Plant: **CN13**

4. **General Data:**
   - Standard Quantity: **1,000** (MOQ)
   - Planned Delivery Time: **30** days
   - Order Unit: **EA**

5. **Conditions:**
   - Condition Type: **PB00** (Gross Price)
   - Amount: **2.35** CNY
   - Currency: **CNY**
   - Unit: **1 EA**
   - Valid From: **2025-02-01**
   - Valid To: Leave blank (no end date)

6. Save info record
7. Create source list entry:
   - Open **Maintain Source List**
   - Material: **PCB-RC3000-MAIN**, Plant: **CN13**
   - Add source: Supplier 1002345
   - Source: **1** (Fixed source - preferred)
   - Valid from: 2025-02-01
   - MRP Indicator: **2** (Relevant for MRP)
   - Save

8. Update material status: **ZB** → **ZC** (ready for costing)

**When MRP runs, it will automatically create PRs for this supplier!**

---

### 5. UPDATE INFO RECORD PRICE

**Example:** Supplier 1002345 raises price from $2.35 to $2.50 for PCB-RC3000-MAIN

**Steps:**
1. Get approved PPCA form with new price
2. Purchasing Manager approves price increase
3. Open **Change Info Record**
4. Search: Material **PCB-RC3000-MAIN**, Supplier **1002345**
5. Go to Conditions tab
6. Add new price line:
   - Valid from: **2025-03-01** (new price effective date)
   - Amount: **2.50** CNY
7. Old price (2.35) automatically gets Valid To = 2025-02-29
8. Save
9. New POs from March 1 will use $2.50

---

## PURCHASE ORDER PROCEDURES

### 6. CREATE PO FROM PURCHASE REQUISITION

**Application:** Create Purchase Order

**Example:** MRP created PR for 5,000 units PCB-RC3000-MAIN

**Steps:**
1. Open **Manage Purchase Requisitions**
2. Filter: Plant **CN13**, Created today
3. Find PR line:
   ```
   PR: 10012345, Item 10
   Material: PCB-RC3000-MAIN
   Quantity: 5,000 EA
   Delivery Date: 2025-03-15
   Source: 1002345 (from source list)
   ```

4. Select PR → Click "Create PO"
5. System creates PO automatically with:
   - Vendor: **1002345** (from source list)
   - Price: **2.35** CNY (from info record)
   - Delivery: 30 days from today
   - Plant: **CN13**
   - Storage Location: **RM01** (Raw Materials)

6. Review PO:
   - Check quantity: 5,000 EA
   - Check price: 2.35 CNY/EA = 11,750 CNY total
   - Check delivery date matches requirement
   - Add delivery instructions if needed

7. Save PO → Note PO number: **4500123456**
8. System emails PO to supplier automatically
9. PR is now "assigned" to PO

**Or manually create PO:**
1. Open **Create Purchase Order**
2. Vendor: **1002345**
3. Company Code: **CN13**, Purch Org: **CN13**
4. Add line: Material **PCB-RC3000-MAIN**, Qty **5,000**, Date **2025-03-15**
5. System fills price from info record
6. Save

---

### 7. EXPEDITE URGENT PO

**Example:** Production needs PCB boards by next week, but PO 4500123456 shows delivery in 3 weeks

**Scenario:** You're the buyer

**Steps:**
1. Open **Display Purchase Order** → Enter **4500123456**
2. Note:
   - Current delivery date: 2025-03-15 (3 weeks away)
   - Need by: 2025-02-25 (next week)
   - Quantity: 5,000 EA

3. Call supplier 1002345:
   - "We need PO 4500123456 by Feb 25, can you expedite?"
   - Supplier checks: "We can do 3,000 pcs by Feb 25, remaining 2,000 by Mar 15"
   - You agree

4. Change PO:
   - Open PO in change mode
   - Split line item:
     - Line 10: 3,000 EA, delivery 2025-02-25
     - Line 20: 2,000 EA, delivery 2025-03-15
   - Save

5. Email production planner: "First 3,000 pcs arriving Feb 25, balance Mar 15"

---

## MRP PROCEDURES

### 8. RUN DAILY MRP

**Application:** Collective MRP Run

**Example:** Daily 8 AM MRP run for CN13 plant

**Steps:**
1. **8:00 AM** - Open **Collective MRP Run**
2. Enter:
   - Plant: **CN13**
   - Processing Key: **NETCH** (Net change - only changed materials)
   - Planning Mode: **1** (Create procurement elements)
   - Create Purchase Req: ✓
   - Schedule Lines: ✓
   - Scheduling: **2** (Lead time scheduling)

3. Click "Execute" → Wait 5-10 minutes
4. MRP runs and creates:
   - Planned orders for materials to produce (FERT, HALB)
   - Purchase requisitions for materials to buy (ROH)

5. Review results:
   - Open **Display Planning File Entries**
   - Plant: **CN13**, Date: Today
   - Check for exception messages

---

### 9. PROCESS MRP EXCEPTIONS

**Example:** MRP exception report shows issues

**Steps:**
1. Open exception list from MRP run
2. Review each exception:

**Exception 1:** "Reschedule Out" - PO 4500234567 for Material M-12345
- Meaning: PO due date is earlier than needed, can be delayed
- Action: Call supplier, ask to delay delivery from Feb 20 to Mar 5
- Change PO delivery date
- Mark exception as processed

**Exception 2:** "Reschedule In" - PO 4500234890 for Material M-67890
- Meaning: PO due date is too late, need it sooner
- Action: Call supplier immediately, request expedite (see procedure 7)
- If can't expedite, inform production of delay
- Mark exception as processed

**Exception 3:** "Cancel Process" - Planned Order for Material RC-2000
- Meaning: No longer needed (customer cancelled order)
- Action: Open planned order, delete it
- Mark exception as processed

3. Process all critical exceptions (shortages first!)
4. Document actions taken
5. Rerun MRP if significant changes made

---

### 10. CONVERT PLANNED ORDER TO PRODUCTION ORDER

**Example:** MRP created planned order for 1,000 units RC-3000

**Steps:**
1. Open **Display Stock/Requirements List**
2. Material: **RC-3000-BK**
3. See planned order:
   ```
   Planned Order: 500123456
   Quantity: 1,000 EA
   Start: 2025-03-01
   Finish: 2025-03-15
   ```

4. Check component availability:
   - Click planned order → Display components
   - All components available? → OK to convert
   - Missing components? → Don't convert yet, expedite PRs first

5. Convert to production order:
   - From planned order, click "Convert"
   - Or open **Create Production Order** and reference planned order
   - System creates firm production order
   - Planned order disappears

6. Production order number: **100234567**
7. Components now reserved
8. Email production planner: "Order 100234567 ready to release"

---

## PRACTICAL SCENARIOS

### Scenario A: New Product Launch

**Situation:** RC-4000 (new model) launching next month, need to set up materials and suppliers

**Your role:** Master Data Team & Buyer

**Timeline:**

**Week 1:**
1. R&D provides BOM with 25 components
2. Check materials in SAP:
   - 10 materials already exist (use for other models)
   - 15 new materials need creation
3. Create 15 new raw material masters (follow procedure 2)
4. Set all to Status ZB

**Week 2:**
1. Commodity Manager negotiates with suppliers
2. Receives quotes for 15 new materials
3. Create 15 info records with prices (procedure 4)
4. Create source list entries
5. Set materials to Status ZC

**Week 3:**
1. Finance runs costing for RC-4000
2. Standard cost calculated: $45.50 per unit
3. Change all material status ZC → ZD
4. Materials ready for MRP

**Week 4:**
1. Sales gets orders for RC-4000
2. MRP runs → Creates PRs for new components
3. You convert PRs to POs
4. Send POs to new suppliers
5. Production can start!

---

### Scenario B: Supplier Quality Issue

**Situation:** QC rejects batch of plastic housings from supplier 1001234, need alternate source

**Your role:** Buyer

**Steps:**
1. QC informs: "Batch from PO 4500456789 rejected, wrong color"
2. You check:
   - Material: HOUSING-BLK (Black housing)
   - Supplier: 1001234
   - Quantity: 10,000 pcs
   - Need date: Next week for production

3. Find alternate supplier:
   - Check source list for HOUSING-BLK
   - Alternate: Supplier 1001567 (also approved)
   - Check info record: They have capacity

4. Create new PO:
   - Supplier: 1001567
   - Material: HOUSING-BLK
   - Quantity: 10,000
   - Delivery: URGENT - 7 days
   - Price: (from info record)

5. Call supplier 1001567:
   - Explain urgent need
   - Confirm they can deliver in 7 days
   - Agree on expedite fee if needed

6. Return to supplier 1001234:
   - Create return purchase order (procedure in MM doc)
   - Arrange pickup of rejected material

7. Update production:
   - New delivery date from alternate supplier
   - Production delays by 3 days

---

### Scenario C: Month-End MRP Run

**Date:** Last day of month

**Your role:** MRP Controller

**8:00 AM:**
1. Run full regenerative MRP (NEUPL not NETCH)
2. Takes 45 minutes for complete run
3. Coffee break...

**9:00 AM:**
1. MRP complete, review results
2. 45 new PRs created
3. 23 exception messages

**9:30 AM:**
1. Process exceptions:
   - 15 "reschedule out" → Email suppliers to delay
   - 5 "reschedule in" → Call suppliers to expedite
   - 3 "cancel" → Delete unnecessary planned orders

**10:30 AM:**
1. Email buyers: "45 new PRs ready for processing"
2. Email production: "4 materials showing shortages, investigating"

**11:00 AM:**
1. Meeting with buyers:
   - Review critical PRs
   - Assign priorities
   - Identify long lead-time items needing immediate POs

**2:00 PM:**
1. Buyers created 30 POs from PRs
2. 15 PRs still pending (negotiations, approvals)
3. Monitor critical materials for production

---

## QUICK REFERENCE

### Plants & Storage Locations
**Plants:**
- CN13 = Suzhou factory
- CN17 = Shanghai warehouse

**Storage Locations:**
- RM01 = Raw Materials
- FG01 = Finished Goods
- PK01 = Packaging Materials
- QI01 = Quality Inspection

### Material Status Codes
- **ZA** = Created (not usable)
- **ZB** = Pending Purchasing (info record needed)
- **ZC** = Pending Costing
- **ZD** = Released (ACTIVE - use this!)
- **ZZ** = Phase-out (discontinuing)

### MRP Types
- **PD** = MRP (system plans automatically)
- **ND** = No planning (manual only)

### Procurement Types
- **E** = In-house production (make)
- **F** = External procurement (buy)

### Purchasing Groups
- P01 = Production Materials
- P02 = Electronic Components
- P03 = Packaging Materials
- P04 = Indirect Materials

### Common Info Record Conditions
- PB00 = Gross Price
- ZB00 = Discount
- FRB1 = Freight

### Key Contacts
- Master Data: [Name] (ext. 1001)
- MRP Controller: [Name] (ext. 1002)
- Commodity Manager: [Name] (ext. 1003)
- System issues: IT Helpdesk (ext. 8888)

---

*End of Purchasing Procedures*

