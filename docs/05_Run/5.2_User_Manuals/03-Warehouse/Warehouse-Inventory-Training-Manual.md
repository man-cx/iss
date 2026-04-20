# Warehouse & Inventory Management Training Manual
## SAP S/4HANA Implementation - Home Control

---

### Document Information
- **Department:** Warehouse & Inventory Management
- **Version:** 1.0
- **Date:** January 2025
- **Target Audience:** Warehouse staff, Inventory controllers, Goods receipt clerks, Pickers/Packers
- **Prerequisites:** Basic computer skills and familiarity with warehouse operations

---

### How to Use This Manual

This training manual is organized by business process. Each process contains step-by-step instructions, tips, and troubleshooting guidance to help you perform your daily warehouse activities in SAP.

---

### Table of Contents

1. Introduction to Warehouse & Inventory in SAP
   - 1.1 Overview of SAP S/4HANA
   - 1.2 How Warehouse Uses SAP
   - 1.3 Key Benefits

2. Getting Started
   - 2.1 Logging into SAP
   - 2.2 Navigating the SAP Interface
   - 2.3 Finding Applications
   - 2.4 Basic Functions

3. Goods Receipt Processes
   - 3.1 Post Goods Receipt from Purchase Order
   - 3.2 Post Goods Receipt from Production Order
   - 3.3 Post Goods Receipt for Returns

4. Goods Issue Processes
   - 4.1 Post Goods Issue for Production Order
   - 4.2 Post Goods Issue for Sales Delivery
   - 4.3 Post Goods Issue for Cost Center

5. Stock Transfer Processes
   - 5.1 Stock Transfer Within Plant (Same Location)
   - 5.2 Stock Transfer Between Plants

6. Inventory Management
   - 6.1 Display Stock Overview
   - 6.2 Display Material Document
   - 6.3 Physical Inventory Count
   - 6.4 Post Physical Inventory Differences

7. Appendices
   - A. Quick Reference Cards
   - B. Common Applications
   - C. Movement Types
   - D. Tips and Tricks
   - E. Frequently Asked Questions
   - F. Support Contacts

---

## SECTION 1: INTRODUCTION

### 1.1 Overview of SAP S/4HANA

SAP S/4HANA is Home Control's enterprise system that manages all business processes. The Warehouse module tracks every movement of materials - from receiving to storage to issuing to customers or production.

**Key Features:**
- Real-time inventory visibility
- Automatic stock updates
- Integrated with purchasing, production, and sales
- Serial number and batch tracking
- Physical inventory management

### 1.2 How Warehouse Uses SAP

Every time materials move in or out of the warehouse, it must be recorded in SAP. This ensures:
- Accurate inventory quantities
- Proper financial accounting (inventory value)
- Traceability for quality and compliance
- Visibility for planning and customer service

**Key Activities in SAP:**
- **Goods Receipt (GR)**: Receiving materials from suppliers or production
- **Goods Issue (GI)**: Issuing materials to production, sales, or other uses
- **Stock Transfers**: Moving materials between locations
- **Physical Inventory**: Counting and reconciling actual stock

**Integration with Other Departments:**
- **Purchasing**: Purchase orders trigger goods receipts
- **Production**: Production orders drive goods issue and receipt
- **Sales**: Deliveries trigger goods issue for shipment
- **Finance**: All movements update inventory value in general ledger
- **Quality**: Quality inspections may block or release stock

### 1.3 Key Benefits

**For Warehouse Department:**
- Paperless transactions (no manual logs)
- Instant inventory visibility
- Reduced errors through system validation
- Clear audit trail of all movements
- Easy lookup of past transactions

**For Home Control:**
- Accurate inventory records enable better planning
- Real-time visibility prevents stockouts
- Proper inventory valuation for financial statements
- Compliance with quality and traceability requirements
- Better customer service through accurate promise dates

---

## SECTION 2: GETTING STARTED

### 2.1 Logging into SAP

**Step-by-Step:**
1. Open web browser (Chrome or Edge)
2. Go to SAP URL: [Company URL]
3. Enter your User ID
4. Enter your Password
5. Click "Log On"

**✏️ Note:** Contact IT if you forget your password.

### 2.2 Navigating the SAP Interface

**SAP Fiori Launchpad** is your home screen with tiles for warehouse applications.

**Key Areas:**
- **Top Bar**: User settings, notifications
- **Tiles**: Applications you can access
- **Search**: Find applications quickly

### 2.3 Finding Applications

**Quick Access Methods:**
- Click tile on home screen
- Use search bar (type "goods receipt")
- Bookmark favorites

### 2.4 Basic Functions

**Common Buttons:**
- **Post** - Save and finalize transaction
- **Check** - Validate before posting
- **Cancel** - Exit without saving
- **Display** - View only (cannot change)
- **Print** - Print labels or documents

**Keyboard Shortcuts:**
- `Enter` - Continue/Execute
- `F3` - Go back
- `Ctrl + S` - Save

---

## SECTION 3: GOODS RECEIPT PROCESSES

### 3.1 POST GOODS RECEIPT FROM PURCHASE ORDER

#### Process Overview

**Purpose:**
Record receipt of materials from suppliers into warehouse inventory. This increases stock quantities and notifies accounts payable that invoice can be paid.

**Business Value:**
Accurate goods receipts ensure inventory is tracked, materials are available for production, and suppliers are paid correctly.

**Frequency:**
Daily - Multiple times per day as supplier deliveries arrive

#### When to Use This Process

You will perform this process when:
- Supplier delivery truck arrives with materials
- You have verified delivery against purchase order
- Quality inspection passed (if required)
- Materials are ready to be put into storage

**Example Scenario:**
A truck from your plastic supplier arrives with 5 boxes of components ordered on PO #4500123456. You check the packing slip, verify quantities and quality, and need to receive the goods into SAP so they're available for production.

#### Who Performs This Process

**Primary Role:** Warehouse Staff (Goods Receipt)

**Related Roles:**
- Quality Inspector - May need to inspect before GR can be posted
- Purchasing - Created the original PO

#### Prerequisites

Before starting this process, ensure you have:
- ✓ Physical delivery from supplier
- ✓ Purchase order number
- ✓ Delivery note/packing slip from supplier
- ✓ Quality inspection passed (if required)
- ✓ Correct storage location identified

**Required Information:**
- Purchase Order number
- Quantity delivered
- Storage location where materials will be stored

#### SAP Application

**Application Name:** Post Goods Receipt

**How to Access:**
- From Fiori Launchpad, click "Post Goods Receipt" tile in "Warehouse" group
- OR search for "Post Goods Receipt"

---

#### Step-by-Step Instructions

#### Step 1: Access Goods Receipt Transaction

**What to do:**
Open the goods receipt application and locate the purchase order.

**Procedure:**
1. Click "Post Goods Receipt" tile or search for it
2. The application opens to entry screen
3. You have two options to find the PO:
   - **Option A**: If you know PO number, enter it directly
   - **Option B**: Search for PO using filters

**For Option B - Searching for PO:**
4. Click "Search" or filter icon
5. Enter search criteria:
   - **Supplier**: Enter supplier name or number
   - **Material**: Enter material number if known
   - **Delivery Date Range**: Expected delivery dates
6. Click "Go" or "Execute"
7. System displays list of open POs with pending receipts
8. Locate your PO in the list
9. Click on the PO to select it

**📸 Screenshot:** Search screen for purchase orders

**💡 TIP:**
> If you have the PO number on the packing slip, entering it directly is fastest. Otherwise, search by supplier name.

---

#### Step 2: Review Purchase Order Details

**What to do:**
Verify the PO matches the physical delivery.

**Procedure:**
1. System displays PO with line items
2. Review each line showing:
   - **Material Number** and **Description**
   - **Ordered Quantity**
   - **Outstanding Quantity** (not yet received)
   - **Unit of Measure**
   - **Delivery Date**
3. Compare with physical delivery:
   - Check material numbers match
   - Verify quantities
   - Confirm unit of measure (EA, KG, M, etc.)
4. If everything matches, proceed to Step 3
5. If there are discrepancies:
   - **Short delivery**: Post only what was delivered
   - **Over delivery**: Check if over-delivery tolerance allows it
   - **Wrong material**: Contact purchasing; do not receive wrong items

**📸 Screenshot:** PO line items display

**🔍 Key Fields:**
- **Material**: Material number - must match delivery
- **Outstanding Qty**: How much is still expected - this is what you can receive
- **Unit**: Make sure you're counting in the right unit (pieces vs. boxes)

**✏️ Note:** If supplier delivered to wrong location or wrong materials, contact Purchasing BEFORE posting GR. Once posted, it's more difficult to correct.

---

#### Step 3: Enter Goods Receipt Quantity

**What to do:**
Enter the quantity actually delivered for each line item.

**Procedure:**
1. For each PO line item, locate the **GR Quantity** field
2. Enter the quantity you physically received
   - If full delivery: Enter the outstanding quantity
   - If partial delivery: Enter only what arrived
   - If no delivery for that item: Leave blank or enter 0
3. **Storage Location**: Verify or select where material will be stored
   - System may propose default storage location
   - Change if storing in different location
   - Common storage locations: FG01 (Finished Goods), RM01 (Raw Materials), etc.
4. **Batch** (if applicable): Enter batch number from supplier's label
5. **Special Stock Indicator**: Usually leave blank (standard stock)
6. Repeat for all line items being received
7. Verify total quantities entered match what was delivered

**📸 Screenshot:** Goods receipt entry screen with quantity fields

**🔍 Key Fields Explained:**
- **GR Quantity**: The amount you're receiving right now. Must be ≤ Outstanding Quantity
- **Storage Location**: Where in the warehouse this will be stored. Important for finding it later!
- **Batch**: For materials with batch management (like chemicals with expiry dates)

**⚠️ IMPORTANT:**
> Only receive what you actually have in hand. Don't post GR for materials not yet delivered - this creates inventory discrepancies.

---

#### Step 4: Enter Delivery Note Information

**What to do:**
Record the supplier's delivery note or packing slip number for reference.

**Procedure:**
1. Locate **Delivery Note** field (may be in header section)
2. Enter the delivery note number from supplier's packing slip
3. **Delivery Date**: Enter date on supplier's delivery document
   - Usually today's date unless backdating
4. **Reference**: Optionally enter truck number, container number, or other reference
5. These fields help with traceability and matching to supplier documents later

**✏️ Note:** Delivery note field is for reference only but very helpful when supplier inquiries arrive.

---

#### Step 5: Check the Goods Receipt

**What to do:**
Validate the GR before posting to catch any errors.

**Procedure:**
1. Click "Check" button (✓ icon) at top of screen
2. System performs validation checks:
   - Quantities within tolerance?
   - Storage locations valid?
   - Materials active and released?
   - Any warnings or errors?
3. **Green Success Message**: GR is valid, ready to post
4. **Yellow Warning**: Review warning but can still post (e.g., "early delivery")
5. **Red Error**: Must fix error before posting
   - Common errors: Invalid storage location, quantity over tolerance
   - Fix the issue and check again
6. Only proceed to posting after successful check

**📸 Screenshot:** Check function results

**💡 TIP:**
> Always use Check function. It catches common mistakes before they become problems.

---

#### Step 6: Post the Goods Receipt

**What to do:**
Finalize the GR, updating inventory and notifying other systems.

**Procedure:**
1. After successful check, click "Post" button
2. System processes the GR (may take a few seconds)
3. Success message appears with:
   - **Material Document Number** (e.g., 5000123456)
   - **Year**
   - Confirmation message
4. **IMPORTANT**: Write down or screenshot the material document number
5. Inventory is immediately updated:
   - Stock quantity increased
   - Value posted to accounting
   - Purchase order outstanding quantity reduced
6. System may trigger:
   - Invoice verification (if GR-based IV setup)
   - Quality inspection (if QM active)
   - Email notification to buyer

**📸 Screenshot:** Success message with material document number

**✅ Expected Result:**
- Green success message: "Material document 5000123456 posted"
- Material document number displayed
- Stock immediately visible in inventory

**🔑 KEY INFORMATION:**
> The material document number is your proof of receipt. Save it! You'll need it for any questions or corrections.

---

#### Step 7: Print Goods Receipt Label

**What to do:**
Print label to attach to physical materials for identification.

**Procedure:**
1. From success screen, click "Print" option
2. Select **Goods Receipt Label** template
3. System generates label with:
   - Material number and description
   - Quantity received
   - GR date and document number
   - Storage location
   - Batch number (if applicable)
4. Print label(s) - usually one per box/pallet
5. Attach labels to physical materials
6. Materials are now properly identified for storage

**📸 Screenshot:** Goods receipt label format

**💡 TIP:**
> If you can't print immediately, write down material document number on delivery note. You can reprint labels later using the document number.

---

#### Step 8: Physical Put-Away

**What to do:**
Move materials to designated storage location and organize for easy retrieval.

**Procedure:**
1. Transport materials to correct storage location (per label)
2. Organize materials:
   - FIFO (first-in-first-out) arrangement
   - Keep similar materials together
   - Ensure labels are visible
3. If using bin locations, note bin location for future reference
4. Verify storage location matches what was entered in SAP
5. Materials are now available for production or sales

**✏️ Note:** While SAP tracks quantity and location, physical organization is still your responsibility for efficient operations.

---

### Verification

**How to verify the process completed successfully:**
1. Material document number was generated
2. Print goods receipt label successfully
3. Check stock in **Display Stock Overview**:
   - Enter material number
   - Select plant and storage location
   - Verify quantity increased by GR quantity
4. Check purchase order:
   - Outstanding quantity reduced
   - GR indicator shows receipt was posted

**Success Indicators:**
- ✓ Material document generated
- ✓ Stock quantity increased in system
- ✓ PO shows GR posted
- ✓ Labels printed and attached
- ✓ Materials in correct physical location

**Where to check:**
- **Display Stock Overview**: See updated inventory
- **Display Material Document**: View GR details
- **Display Purchase Order**: Confirm receipt recorded

---

### Tips and Best Practices

💡 **Efficiency Tips:**
- Have PO number ready before starting - write it on delivery note when truck arrives
- Receive full deliveries when possible - partial receipts create more work
- Process GRs as soon as materials arrive - delays affect production planning
- Use batch receive for multiple POs from same supplier

💡 **Accuracy Tips:**
- Always count materials physically - don't trust supplier's count alone
- Check material numbers match exactly (don't assume)
- Verify storage location before posting - easier to correct before GR
- Take photos of delivery if there are damages or discrepancies

💡 **Things to Avoid:**
- ❌ Don't post GR for materials not yet received - creates false inventory
- ❌ Don't receive damaged materials without noting in system
- ❌ Don't skip the Check function - catches errors
- ❌ Don't forget to print labels - unlabeled materials get lost
- ❌ Don't put materials in wrong location - defeats inventory tracking

---

### Common Issues and Solutions

#### Issue 1: "Quantity exceeds over-delivery tolerance" error

**Symptom:** Cannot post GR; red error about over-delivery

**Cause:** Supplier delivered more than allowed tolerance (usually 10%)

**Solution:**
1. Reduce GR quantity to maximum allowed
2. Set aside excess materials
3. Inform Purchasing of over-delivery
4. Buyer will decide: Return excess OR create new PO for excess quantity

---

#### Issue 2: Material not found or blocked

**Symptom:** Error message says material is blocked or doesn't exist

**Cause:** Material status not released, or material not extended to this plant

**Solution:**
1. Note material number from delivery
2. Contact Master Data Team or Purchasing
3. They will check material status
4. If blocked, find out why (phase-out? quality hold?)
5. If not extended to plant, Master Data Team can extend it
6. Once resolved, post GR

---

#### Issue 3: Wrong storage location selected

**Symptom:** Posted GR but realized storage location is wrong

**Cause:** Selected wrong location from dropdown

**Solution:**
1. Note material document number
2. Use **Post Goods Movement** to transfer stock from wrong location to correct location
3. Movement type 311 (stock transfer)
4. Enter material, from location (wrong), to location (correct), quantity
5. Post transfer
6. Physically move materials to correct location
7. Inform supervisor of correction made

---

#### Issue 4: Posted wrong quantity

**Symptom:** GR posted but quantity is incorrect

**Cause:** Typo during entry or miscounted

**Solution:**
1. **If too much posted**: Cannot undo GR, but can post goods issue to correct (movement type 102)
2. **If too little posted**: Post additional GR for remaining quantity using same PO
3. Always document corrections for audit trail
4. Inform Purchasing if significant difference from PO
5. Physical inventory count will eventually reconcile if small difference

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Application Name | Post Goods Receipt |
| Frequency | Multiple times daily |
| Primary Role | Warehouse Staff (Goods Receipt) |
| Processing Time | 5-10 minutes per receipt |
| Prerequisites | PO number, physical delivery, storage location |

**Key Fields:**
- **Purchase Order**: PO number from packing slip
- **GR Quantity**: Amount physically received
- **Storage Location**: Where materials will be stored
- **Delivery Note**: Supplier's packing slip number

**Common Storage Locations:**
- RM01: Raw Materials
- FG01: Finished Goods
- PK01: Packaging Materials
- QI01: Quality Inspection

**Critical Steps:**
1. Find PO
2. Count materials
3. Enter quantity and location
4. Check before posting
5. Post and save document number
6. Print label
7. Put away materials

---

### 3.2 POST GOODS RECEIPT FROM PRODUCTION ORDER

[Process continues with same detailed format for production order GR...]

---

## SECTION 4: GOODS ISSUE PROCESSES

### 4.1 POST GOODS ISSUE FOR PRODUCTION ORDER

[Process continues...]

---

## SECTION 5: STOCK TRANSFER PROCESSES

[Processes continue...]

---

## SECTION 6: INVENTORY MANAGEMENT

### 6.1 DISPLAY STOCK OVERVIEW

[Process continues...]

### 6.3 PHYSICAL INVENTORY COUNT

#### Process Overview

**Purpose:**
Perform physical counting of inventory to verify SAP quantities match actual stock on hand. Reconcile differences and update system to reflect true inventory.

**Business Value:**
Physical inventory ensures inventory accuracy for financial reporting, identifies shrinkage or losses, maintains data integrity for planning, and meets audit requirements.

**Frequency:**
- **Cycle counting**: Weekly or monthly for selected materials
- **Full physical inventory**: Quarterly or annually for all materials

#### When to Use This Process

You will perform this process when:
- Scheduled physical inventory date arrives
- Finance requests inventory count for period close
- Significant discrepancies suspected in certain materials
- Audit requirements mandate inventory verification
- New warehouse setup or reorganization

**Example Scenario:**
End of quarter approaches. Finance requires physical count of all raw materials inventory for financial statements. You print count sheets, perform physical count with team, enter results in SAP, and post differences to reconcile system with actual.

#### Who Performs This Process

**Primary Roles:**
- **Inventory Controller** - Plans and schedules counts, enters results, analyzes differences
- **Warehouse Staff** - Performs physical counting

#### Prerequisites

Before starting this process, ensure you have:
- ✓ Physical inventory scheduled and planned
- ✓ Count team assigned
- ✓ Materials organized and labeled
- ✓ Stock movements frozen during count (if possible)
- ✓ Count sheets ready

**Required Information:**
- Plant and storage location to count
- Materials to count (all or selected)
- Count date
- Count team members

#### SAP Applications

**Application Name:** 
- Create Physical Inventory Document
- Enter Physical Inventory Count
- Post Physical Inventory Difference

**How to Access:**
- From Fiori Launchpad, search for "Physical Inventory"

---

#### Step-by-Step Instructions

#### Step 1: Create Physical Inventory Document

**What to do:**
Create the inventory document in SAP that defines what will be counted.

**Procedure:**
1. Open **Create Physical Inventory Document** application
2. Enter header information:
   - **Plant**: Select plant where count will occur
   - **Storage Location**: Select location(s) to count
   - **Physical Inventory Date**: Date of the count
   - **Document Date**: Today's date
3. Select count scope:
   - **All materials**: Full physical inventory
   - **Material range**: Specific materials (cycle count)
   - **Material group**: All materials in a group
4. **Count Type**:
   - Standard count (count all quantities)
   - Sample count (verify selected items)
5. Click "Execute" or "Create"
6. System generates physical inventory document
7. Note the **Physical Inventory Document Number** (e.g., PI-2025-001)
8. System creates list of all materials in scope

**📸 Screenshot:** Physical inventory document creation screen

**💡 TIP:**
> For large warehouses, break count into sections by storage location. Multiple PI documents can run simultaneously in different areas.

---

#### Step 2: Print Count Sheets

**What to do:**
Print count sheets for warehouse staff to record physical counts.

**Procedure:**
1. From physical inventory document, click "Print Count Sheets"
2. Select print format:
   - **With book quantity**: Shows SAP quantity (not recommended - may bias counters)
   - **Without book quantity**: Blind count (recommended - more accurate)
3. Sort order:
   - By material number
   - By storage bin location
4. Click "Print"
5. System generates count sheets showing:
   - Physical inventory document number
   - Material number and description
   - Storage location
   - Blank space for counted quantity
   - Counter signature line
6. Distribute count sheets to count team

**📸 Screenshot:** Physical inventory count sheet

**✏️ Note:** Blind counts (without SAP quantity shown) are more accurate because counters aren't influenced by expected quantities.

---

#### Step 3: Perform Physical Count

**What to do:**
Count team physically counts materials and records on count sheets.

**Procedure:**
1. Count team goes to storage location with count sheets
2. For each material on count sheet:
   - Locate material in warehouse
   - Count all quantities in all bins/locations
   - Record count on sheet
   - Write unit of measure (EA, KG, etc.)
   - Sign or initial
3. Count tips:
   - Count systematically (left to right, top to bottom)
   - Don't skip materials - zero count is valid
   - Double-check high-value or critical materials
   - Tag counted areas to avoid recounting
   - Note any discrepancies or damaged goods
4. If material not found (SAP says exists but not in location):
   - Write "NOT FOUND" on count sheet
   - Check adjacent areas
   - Note for investigation
5. After counting complete, team leader reviews count sheets for completeness

**📸 Screenshot:** Warehouse staff counting with count sheet

**💡 TIP:**
> Two-person count teams reduce errors. One counts, one records. Switch roles halfway through.

---

#### Step 4: Enter Count Results in SAP

**What to do:**
Inventory Controller enters physical count results into SAP system.

**Procedure:**
1. Open **Enter Physical Inventory Count** application
2. Enter **Physical Inventory Document Number**
3. System displays list of materials in document
4. For each material, enter:
   - **Counted Quantity**: What was physically counted
   - **Unit of Measure**: Confirm unit (EA, KG, etc.)
   - **Counter**: Person who counted
   - **Count Date**: Actual date counted
5. System automatically compares count to book (SAP) quantity
6. Differences are highlighted:
   - **Green**: Counted quantity matches book
   - **Yellow**: Small difference (within tolerance)
   - **Red**: Significant difference (requires investigation)
7. Review all entries for data entry errors
8. Save count results

**📸 Screenshot:** Count entry screen showing differences

**🔍 Key Fields:**
- **Counted Qty**: Enter exactly what count sheet says - don't "adjust" to match SAP
- **Difference**: System calculates = Counted - Book quantity
- **Positive difference**: More inventory than SAP shows
- **Negative difference**: Less inventory than SAP shows (shrinkage)

**⚠️ IMPORTANT:**
> Enter counts exactly as written on count sheets. Don't adjust numbers to match SAP expectations. The purpose is to find differences!

---

#### Step 5: Investigate Significant Differences

**What to do:**
For materials with large variances, investigate before posting.

**Procedure:**
1. Review all materials with significant differences
2. For each variance:
   - **Check count sheet**: Is count legible? Was unit correct?
   - **Recount material**: Send team back to verify count
   - **Check recent transactions**: Were there GRs or GIs during count period?
   - **Check other locations**: Is material in wrong storage location?
   - **Check material document**: Was there data entry error in past transaction?
3. **Common causes of differences**:
   - Scrap or damage not recorded
   - Materials issued but not posted in SAP
   - Materials received but not yet posted
   - Materials in wrong location (show as missing in one, excess in another)
   - Data entry errors in past transactions
4. Document investigation findings
5. If recount needed, update count in SAP
6. Obtain supervisor approval for large differences before posting

**✏️ Note:** Some companies require management approval for differences exceeding certain thresholds (e.g., $5,000 or 10% variance).

---

#### Step 6: Post Physical Inventory Differences

**What to do:**
Post inventory differences to update SAP quantities to match physical count.

**Procedure:**
1. After all counts entered and verified, open **Post Physical Inventory Difference**
2. Enter **Physical Inventory Document Number**
3. System displays all materials with differences
4. Review the posting:
   - **Positive differences**: System will increase inventory (debit inventory, credit inventory adjustment account)
   - **Negative differences**: System will decrease inventory (credit inventory, debit inventory adjustment/loss account)
5. For each difference, system shows:
   - Material
   - Book quantity (SAP before count)
   - Counted quantity
   - Difference
   - Value impact
6. Click "Post"
7. System posts differences:
   - Inventory quantities updated in SAP to match count
   - Material documents created for differences
   - GL postings made for value changes
8. Success message displays with material document numbers
9. Save/print summary of postings

**📸 Screenshot:** Physical inventory difference posting screen

**✅ Expected Result:**
- All counted materials now show count quantity in SAP
- Differences posted as inventory adjustments
- GL accounts reflect value changes

---

#### Step 7: Analyze and Report Results

**What to do:**
Generate reports and analyze inventory accuracy.

**Procedure:**
1. Run **Physical Inventory Analysis Report**
2. Review metrics:
   - Total items counted
   - Items with differences
   - Value of differences
   - Accuracy percentage
3. Identify trends:
   - Which materials frequently have differences?
   - Which storage locations have issues?
   - Shrinkage patterns
4. Create action plan:
   - Improve processes for problem materials
   - Increase cycle count frequency for critical items
   - Address root causes (security, process compliance)
5. File physical inventory documentation for audit

**📸 Screenshot:** Physical inventory analysis report

---

### Verification

**How to verify the process completed successfully:**
1. All materials on count sheets have counts entered in SAP
2. Differences investigated and explained
3. Posting successful with material document numbers
4. Stock quantities in **Display Stock Overview** match counted quantities
5. Documentation filed

**Success Indicators:**
- ✓ Physical inventory document status = "Completed"
- ✓ All differences posted
- ✓ SAP quantities = Physical counts
- ✓ GL postings successful
- ✓ Report generated

---

### Tips and Best Practices

💡 **Planning Tips:**
- Schedule counts during low-activity periods (weekends, evenings)
- Freeze stock movements during count if possible (no GRs/GIs)
- Communicate count schedule to all departments in advance
- Ensure all materials are properly labeled before count

💡 **Counting Tips:**
- Use two-person teams for accuracy
- Blind counts (don't show book quantity) are more accurate
- Count systematically to avoid missing areas
- Recount high-value items for accuracy
- Take photos of unusual situations

💡 **Things to Avoid:**
- ❌ Don't show counters the SAP quantities - biases count
- ❌ Don't adjust counts to match SAP without physical verification
- ❌ Don't skip investigating large differences
- ❌ Don't post differences without management approval for high values
- ❌ Don't perform counts during busy production/shipping periods

---

### Common Issues and Solutions

#### Issue 1: Large discrepancy found

**Symptom:** Counted quantity significantly different from SAP

**Cause:** Could be many reasons - scrap, theft, location errors, data entry errors

**Solution:**
1. Recount the material immediately
2. Check recent transactions for this material
3. Search other storage locations (may be misplaced)
4. Review past GRs and GIs for errors
5. If recount confirms difference, investigate root cause
6. Document findings
7. Get management approval before posting if above threshold
8. Post difference after approval

---

#### Issue 2: Material not found in location

**Symptom:** SAP shows inventory in location but can't find it physically

**Cause:** Material moved but not recorded, or wrong location in SAP

**Solution:**
1. Search nearby locations and bins
2. Check if material has distinctive appearance (ask team if seen)
3. Check recent GIs - maybe already issued but still showing in SAP
4. Review past GRs - was location entered correctly?
5. If truly not found, count as zero (shrinkage/loss)
6. Document as missing for investigation
7. Post negative difference
8. Report for security/process review

---

#### Issue 3: Cannot post differences - period closed

**Symptom:** Error message says posting period is closed

**Cause:** Finance closed the period for month-end

**Solution:**
1. Contact Finance/GL team
2. Request period reopening temporarily
3. Or wait until next period opens
4. Post differences once period is open
5. Note: This affects which month the adjustment impacts

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Applications | Create PI Doc, Enter Count, Post Difference |
| Frequency | Quarterly/Annually (full); Weekly/Monthly (cycle) |
| Primary Role | Inventory Controller, Warehouse Staff |
| Processing Time | Varies by scope - Full warehouse may take 1-2 days |
| Prerequisites | PI schedule, count team, organized warehouse |

**Process Flow:**
1. Create PI Document
2. Print Count Sheets
3. Physical Count
4. Enter Counts in SAP
5. Investigate Differences
6. Post Differences
7. Analyze Results

**Key Concepts:**
- **Book Quantity**: What SAP shows before count
- **Counted Quantity**: What was physically counted
- **Difference**: Counted - Book
- **Positive Diff**: Found more than expected (gain)
- **Negative Diff**: Found less than expected (loss/shrinkage)

---

## APPENDICES

### Appendix A: Quick Reference Cards

**Goods Receipt from PO - Quick Steps:**
1. Open Post Goods Receipt
2. Enter PO number
3. Enter GR quantity and storage location
4. Check
5. Post
6. Print label
7. Put away

**Goods Issue for Production - Quick Steps:**
1. Open Post Goods Issue
2. Enter Production Order number
3. Verify materials and quantities
4. Post
5. Print picking list

**Physical Inventory - Quick Steps:**
1. Create PI Document
2. Print count sheets
3. Count physically
4. Enter counts in SAP
5. Investigate differences
6. Post differences

### Appendix B: Common Applications

| **Application** | **Purpose** | **When to Use** |
|-----------------|-------------|-----------------|
| Post Goods Receipt | Receive materials | Supplier delivery arrives |
| Post Goods Issue | Issue materials | Production needs components |
| Display Stock Overview | Check inventory | Need to know stock level |
| Post Goods Movement | Transfer stock | Move between locations |
| Display Material Document | View past transactions | Research a movement |
| Physical Inventory | Count inventory | Scheduled PI count |

### Appendix C: Movement Types (Reference)

| **Movement Type** | **Description** | **When Used** |
|-------------------|-----------------|---------------|
| 101 | GR for PO | Receiving from supplier |
| 102 | GR Reversal | Cancel wrong GR |
| 201 | GI to Cost Center | Issue for consumption |
| 261 | GI to Production Order | Components to production |
| 311 | Transfer Posting | Between storage locations |
| 501 | GR without PO | Receipt without reference |
| 551 | GI for Scrapping | Dispose of scrap |
| 601 | GI for Delivery | Ship to customer |

### Appendix D: Tips and Tricks

**Speed Tips:**
- Use Enter key to move between fields faster than clicking
- Learn your most common storage locations to type quickly
- Bookmark frequently used applications
- Process similar transactions in batches

**Accuracy Tips:**
- Always verify material number matches label
- Double-check quantities for expensive materials
- Use Check function before every post
- Print labels immediately so you don't forget

**Organization Tips:**
- Keep work area tidy - easy to count accurately
- Use FIFO (first-in-first-out) arrangement
- Label everything clearly
- Consolidate partial boxes when possible

### Appendix E: Frequently Asked Questions

**Q: What if I posted a goods receipt to the wrong storage location?**
A: Use movement type 311 to transfer the stock from wrong location to correct location. Then physically move the materials.

**Q: Can I reverse a goods receipt after posting?**
A: Yes, use movement type 102 (GR reversal) with the original material document number. But this should only be done for errors, not normal processing.

**Q: What if the quantity on the packing slip doesn't match what I count?**
A: Always post what you physically count. Note the discrepancy and inform Purchasing. They will handle the discrepancy with the supplier.

**Q: How do I know which storage location to use?**
A: Each material type has standard locations (RM01 for raw materials, FG01 for finished goods). Check with your supervisor if unsure.

**Q: What if I forget the material document number?**
A: You can look it up later using Display Material Document. Search by material number and date range.

### Appendix F: Support Contacts

**For SAP Technical Issues:**
- IT Help Desk: helpdesk@homecontrol.com
- Phone: +XX-XXXX-XXXX

**For Process Questions:**
- Warehouse Supervisor: [Name and contact]
- Inventory Controller: [Name and contact]
- Purchasing (for PO issues): [Name and contact]

**Training Resources:**
- Training materials: [Shared folder location]
- Video tutorials: [URL]

---

**Document Revision History**

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | January 2025 | Training Development Team | Initial Warehouse Training Manual |

---

*End of Warehouse & Inventory Management Training Manual*

