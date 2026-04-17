# Production Planning Training Manual
## SAP S/4HANA Implementation - Home Control

---

### Document Information
- **Department:** Production Planning & Control
- **Version:** 1.0
- **Date:** January 2025
- **Target Audience:** Production planners, MRP controllers, Production supervisors, BOM engineers
- **Prerequisites:** Basic computer skills and familiarity with production processes

---

### Table of Contents

1. Introduction to Production Planning in SAP
2. Getting Started
3. Master Data Processes
   - 3.1 Maintain Bill of Material (BOM)
   - 3.2 Maintain Routing
4. Material Requirements Planning (MRP)
   - 4.1 Run MRP
   - 4.2 Evaluate MRP Results
   - 4.3 Process MRP Exceptions
5. Production Order Management
   - 5.1 Create Production Order
   - 5.2 Release Production Order
   - 5.3 Confirm Production Order
   - 5.4 Goods Receipt from Production
   - 5.5 Technically Complete and Settle Production Order
6. Appendices

---

## SECTION 1: INTRODUCTION

### 1.1 Overview

SAP S/4HANA Production Planning (PP) module manages the complete manufacturing cycle from material planning through production execution to finished goods receipt.

**Key Features:**
- Material Requirements Planning (MRP)
- Bill of Material (BOM) management
- Routing and work center management
- Production order management
- Capacity planning
- Production confirmation
- Integration with inventory and costing

### 1.2 How Production Uses SAP

**Key Activities:**
- **Master Data**: Maintain BOMs, routings, work centers
- **Planning**: Run MRP to calculate material and production requirements
- **Execution**: Create and release production orders
- **Confirmation**: Record production output and consumption
- **Costing**: Settle production order costs

**Integration:**
- **Sales**: Customer orders create demand in MRP
- **Purchasing**: MRP generates purchase requisitions for components
- **Warehouse**: Production orders drive goods issue and receipt
- **Finance**: Production order settlement posts costs and variances
- **Quality**: Quality inspections can block production or finished goods

### 1.3 Key Benefits

**For Production Department:**
- Automated material requirements calculation
- Clear production schedule and priorities
- Integrated component availability checking
- Real-time production status visibility
- Reduced paperwork with electronic orders

**For Home Control:**
- Optimized inventory levels
- Reduced stockouts and production delays
- Better capacity utilization
- Accurate production costing
- Improved on-time delivery performance

---

## SECTION 2: GETTING STARTED

[Standard login and navigation information similar to other manuals...]

---

## SECTION 3: MASTER DATA PROCESSES

### 3.1 MAINTAIN BILL OF MATERIAL (BOM)

#### Process Overview

**Purpose:**
Create and maintain Bill of Materials (BOMs) which define the components and quantities required to manufacture a product.

**Business Value:**
BOMs are the foundation of production planning, material requirements calculation, and product costing. Accurate BOMs ensure correct materials are ordered and issued to production.

**Frequency:**
As needed - when new products designed or existing BOMs change.

#### When to Use This Process

- R&D designs new product
- Engineering changes to existing product
- Component substitution
- BOM corrections needed

**Example Scenario:**
R&D designs new remote control model RC-3000. You need to create BOM listing all components (PCB boards, plastic housing, buttons, packaging, etc.) with quantities so MRP can calculate requirements and production can build it.

#### Who Performs This Process

**Primary Role:** BOM Engineer (R&D), Master Data Team

#### Step-by-Step Instructions

#### Step 1: Prepare BOM Information

**What to do:**
Gather complete list of components from engineering design.

**Procedure:**
1. R&D provides product design with component list
2. For each component collect:
   - Material number
   - Quantity per finished good
   - Unit of measure
   - Scrap percentage (if applicable)
   - Position in assembly sequence
3. Verify all component materials exist in SAP material master
4. Identify any alternative components (substitutions)

---

#### Step 2: Create BOM Header

**What to do:**
Create BOM in SAP for the finished good material.

**Procedure:**
1. Open **Maintain Bill of Material** application
2. Click "Create"
3. Enter:
   - **Material**: Finished goods material number (e.g., RC-3000)
   - **Plant**: Manufacturing plant (CN13, CN17, etc.)
   - **BOM Usage**: 1 (Production)
   - **Valid From**: Effective date
4. Enter header data:
   - **Base Quantity**: Usually 1 (quantity of FG this BOM produces)
   - **Base Unit**: EA (each)
   - **Status**: Under development initially
5. Save header

**📸 Screenshot:** BOM header entry

---

#### Step 3: Add Component Line Items

**What to do:**
Add all components to the BOM with quantities.

**Procedure:**
1. In BOM components section, add first component
2. For each component enter:
   - **Item Number**: Sequential (10, 20, 30...)
   - **Component Material**: Material number
   - System shows material description
   - **Quantity**: Quantity needed per base quantity of FG
   - **Unit**: Usually EA, but could be KG, M, etc.
   - **Item Category**: L (stock item) most common
   - **Procurement Type**: From material master (Make or Buy)
3. Optional fields:
   - **Scrap %**: If component has typical scrap rate
   - **Assembly**: If multi-level BOM, which assembly this belongs to
   - **Position**: Physical location in product
4. Repeat for all components
5. Verify all materials listed
6. Check quantities carefully

**📸 Screenshot:** BOM component entry

**🔍 Key Fields:**
- **Component**: Material to be consumed
- **Quantity**: How many per finished good
- **Scrap %**: Extra to account for waste (e.g., 5% scrap means order 105 to get 100 good)

---

#### Step 4: Define BOM Validity and Usage

**What to do:**
Set when BOM is effective and for what purposes.

**Procedure:**
1. **Valid From Date**: When BOM becomes active
2. **Valid To Date**: Usually leave blank (valid indefinitely)
3. **BOM Status**:
   - 1 = Under development (not used in production yet)
   - 4 = Active/Released (use in production)
4. **BOM Usage**:
   - 1 = Production (most common)
   - 2 = Engineering
   - 5 = Costing
5. For new BOM, keep status = 1 until verified
6. After testing/approval, change status to 4 (Active)

---

#### Step 5: Release BOM for Production

**What to do:**
Activate BOM so it can be used in production orders and MRP.

**Procedure:**
1. Review BOM completeness:
   - All components listed?
   - Quantities correct?
   - Scrap percentages reasonable?
2. Obtain approval from R&D and Production
3. Change BOM status from 1 to 4 (Active)
4. Set **Valid From** date (usually today or future production start date)
5. Save BOM
6. BOM now active and will be used:
   - In MRP calculations
   - When creating production orders
   - For product costing

**✅ Expected Result:**
- BOM status = 4 (Active)
- BOM appears when creating production orders for this FG
- MRP calculates component requirements based on this BOM

---

### Tips and Best Practices

💡 **Accuracy Tips:**
- Verify all component material numbers exist before creating BOM
- Double-check quantities - BOM errors multiply across all production orders
- Use consistent units of measure
- Update BOMs promptly when engineering changes occur

💡 **Version Control:**
- When making significant BOM changes, consider creating new BOM version
- Keep history of BOM changes for traceability
- Document reason for changes (ECN - Engineering Change Notice)

💡 **Things to Avoid:**
- ❌ Don't release BOM before all components verified
- ❌ Don't use incorrect units (EA vs PC confusion)
- ❌ Don't forget scrap percentages for high-waste components
- ❌ Don't leave outdated BOMs active

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Application | Maintain Bill of Material |
| Frequency | As needed |
| Role | BOM Engineer, Master Data Team |
| Time | 30-60 minutes depending on complexity |

**Critical Fields:**
- Material (FG)
- Plant
- Component Material
- Component Quantity
- BOM Status (1=Dev, 4=Active)
- Valid From Date

---

### 3.2 MAINTAIN ROUTING

[Process for creating production routings with operations and work centers...]

---

## SECTION 4: MATERIAL REQUIREMENTS PLANNING (MRP)

### 4.1 RUN MRP

#### Process Overview

**Purpose:**
Execute Material Requirements Planning to calculate what materials need to be procured or produced based on demand (sales orders, forecasts, stock requirements).

**Business Value:**
MRP automates planning, ensuring materials are available when needed while minimizing excess inventory. It generates planned orders for production and purchase requisitions for purchased materials.

**Frequency:**
Daily or multiple times per day depending on business dynamics.

#### When to Use This Process

- Daily scheduled MRP run
- After receiving large customer orders
- When stock levels change significantly
- After BOM or lead time changes
- Before production planning meetings

**Example Scenario:**
New customer orders arrived overnight for 10,000 units of RC-2000. You run MRP to calculate component requirements, check availability, and generate planned orders for production and purchase requisitions for materials to buy.

#### Who Performs This Process

**Primary Role:** MRP Controller, Production Planner

#### Step-by-Step Instructions

#### Step 1: Determine MRP Scope

**What to do:**
Decide which materials to include in MRP run.

**Options:**
1. **Full MRP Run**: All materials in plant (overnight batch)
2. **Single-Item MRP**: One specific material
3. **MRP by Material Group**: Product family or category
4. **Net Change MRP**: Only materials with changes since last run

**For Daily Planning:**
- Usually run net change MRP during day (faster)
- Full MRP overnight (comprehensive)

---

#### Step 2: Execute MRP Run

**What to do:**
Run the MRP calculation.

**Procedure:**
1. Open **Single-Item, Multi-Level MRP** (for single material) OR
2. Open **Collective MRP Run** (for multiple materials)
3. Enter selection criteria:
   - **Plant**: Your manufacturing plant
   - **MRP Controller**: Your planner ID (optional, for filtering)
   - **Material**: If single item
   - **Processing Key**: NETCH (net change) or NEUPL (regenerative)
4. **Planning Mode**:
   - 1 = Create procurement proposals (planned orders, PRs)
   - 2 = Simulate only (no proposals created)
5. **Scheduling**:
   - 1 = Basic dates
   - 2 = Lead time scheduling
   - 3 = Capacity requirements
6. Click "Execute" or "Run"
7. System performs MRP calculation:
   - Reads demand (sales orders, forecasts)
   - Checks current stock
   - Checks scheduled receipts (POs, production orders)
   - Calculates net requirements
   - Creates planned orders / purchase requisitions
   - Generates exception messages
8. Wait for completion (seconds to minutes depending on scope)
9. Review completion message

**📸 Screenshot:** MRP run selection screen

**💡 TIP:**
> Run single-item MRP for urgent materials. Run collective MRP for comprehensive planning.

---

#### Step 3: Review MRP Results

**What to do:**
Check what MRP created and identify actions needed.

**Procedure:**
1. Open **Evaluating MRP Results** application
2. Or use **Display Stock/Requirements List** for specific material
3. Enter material number
4. System shows:
   - **Demand**: Sales orders, forecasts
   - **Stock**: Current inventory
   - **Receipts**: Scheduled POs and production orders
   - **Requirements**: What MRP calculated is needed
   - **Procurement Proposals**: Planned orders and PRs created
5. Review each material:
   - Are planned orders reasonable?
   - Are quantities correct?
   - Are dates achievable?
6. Check for exception messages (see Step 4)

**📸 Screenshot:** Stock/requirements list

**🔍 Key Information:**
- **Green**: Stock sufficient
- **Yellow**: Stock low but planned
- **Red**: Shortage - action needed

---

#### Step 4: Process MRP Exception Messages

**What to do:**
Review and resolve MRP exception messages.

**Procedure:**
1. Open **Display Planning File Entries** or exception monitor
2. System shows exceptions like:
   - **Reschedule In**: PO or order should be expedited
   - **Reschedule Out**: PO or order can be delayed
   - **Cancel**: Planned order no longer needed
   - **Increase Quantity**: Need more
   - **Reduce Quantity**: Need less
   - **Missing Parts**: Components not available
3. For each exception:
   - Understand the cause
   - Take action:
     - Reschedule: Contact supplier or change production date
     - Cancel: Delete planned order
     - Quantity change: Modify order
4. Process systematically by priority (shortages first)

**📸 Screenshot:** MRP exception messages

**⚠️ IMPORTANT:**
> Don't ignore exception messages! They highlight problems that will cause shortages or excess inventory.

---

#### Step 5: Convert Planned Orders to Production Orders

**What to do:**
Convert planned orders (MRP proposals) into firm production orders.

**Procedure:**
1. Review planned orders from MRP
2. For each planned order to convert:
   - Verify material availability of components
   - Confirm capacity available
   - Check timing makes sense
3. Options to convert:
   - **Manual**: Go to **Create Production Order**, reference planned order
   - **Mass conversion**: Use collective conversion transaction
4. After conversion:
   - Planned order becomes firm production order
   - Components reserved
   - Order visible to production floor
5. Production orders can now be released and executed

**✏️ Note:** Some companies auto-convert within certain time fence. Others require manual review before conversion.

---

#### Step 6: Process Purchase Requisitions

**What to do:**
Review purchase requisitions created by MRP and route to purchasing.

**Procedure:**
1. MRP automatically creates PRs for purchased materials
2. Open **Manage Purchase Requisitions**
3. Filter by:
   - Plant
   - MRP Controller
   - Creation date (today)
4. Review each PR:
   - Material correct?
   - Quantity reasonable?
   - Date achievable?
5. PRs are automatically routed to Purchasing department
6. Buyers will convert PRs to purchase orders
7. Monitor critical PRs to ensure timely conversion

**✏️ Note:** This process detailed in Purchasing Training Manual.

---

### Verification

**How to verify MRP ran successfully:**
1. MRP completion message displayed
2. Planned orders visible in **Display Stock/Requirements List**
3. Purchase requisitions created (check **Manage Purchase Requisitions**)
4. Exception messages reviewed and documented
5. No critical shortages remaining

**Success Indicators:**
- ✓ MRP completed without errors
- ✓ Planned orders generated
- ✓ PRs created for purchased items
- ✓ Exception messages processed
- ✓ Material availability improved

---

### Tips and Best Practices

💡 **Planning Tips:**
- Run MRP daily at consistent time (e.g., 8 AM)
- Process exceptions immediately after MRP run
- Coordinate with Purchasing on critical PRs
- Review planned orders before auto-conversion

💡 **Accuracy Tips:**
- Keep master data current (lead times, lot sizes, safety stocks)
- Clean up old planned orders regularly
- Verify BOMs are accurate
- Update material status promptly

💡 **Things to Avoid:**
- ❌ Don't ignore exception messages
- ❌ Don't run MRP during production order processing (timing conflicts)
- ❌ Don't convert all planned orders blindly
- ❌ Don't forget to check component availability before releasing orders

---

### Common Issues and Solutions

#### Issue 1: MRP creates too many small planned orders

**Symptom:** MRP generates many planned orders for tiny quantities

**Cause:** Lot size parameter set to "lot-for-lot" instead of minimum or fixed lot size

**Solution:**
1. Review material master MRP view
2. Change lot size parameter:
   - From LFX (lot-for-lot) to
   - FX (fixed lot size) with minimum quantity
   - Or HB (economic order quantity)
3. Run MRP again
4. Orders will be consolidated

---

#### Issue 2: MRP not creating planned orders for material

**Symptom:** Material shows shortage but no planned orders created

**Cause:** MRP type set to "ND" (No Planning) or material blocked

**Solution:**
1. Check material master MRP view
2. Verify MRP Type = PD (MRP)
3. Check material status (should be ZD - Released)
4. Verify plant set correctly
5. Run MRP again for this material

---

#### Issue 3: Exception message "Missing parts"

**Symptom:** Cannot release production order - components not available

**Cause:** Components not in stock and not on order

**Solution:**
1. Display stock/requirements list for missing component
2. Check if component has planned orders or PRs
3. If yes, expedite those orders
4. If no, run MRP for component
5. Contact Purchasing for emergency procurement if critical

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Application | Single-Item MRP / Collective MRP Run |
| Frequency | Daily or multiple times daily |
| Role | MRP Controller, Production Planner |
| Time | 10-30 minutes depending on exceptions |

**MRP Process Flow:**
1. Run MRP
2. Review results
3. Process exceptions
4. Convert planned orders to production orders
5. Monitor PRs conversion by Purchasing

**Key Concepts:**
- **Demand**: What's needed (sales orders, forecasts)
- **Stock**: What's available
- **Receipts**: What's coming (POs, production orders)
- **Net Requirement**: Demand - Stock - Receipts
- **Planned Order**: MRP proposal to produce
- **Purchase Requisition**: MRP proposal to buy

---

## SECTION 5: PRODUCTION ORDER MANAGEMENT

### 5.1 CREATE PRODUCTION ORDER

[Process for creating production orders manually or from planned orders...]

### 5.2 RELEASE PRODUCTION ORDER

[Process for releasing orders to shop floor...]

### 5.3 CONFIRM PRODUCTION ORDER

[Process for recording production output and time...]

### 5.4 GOODS RECEIPT FROM PRODUCTION

[Process for receiving finished goods into inventory...]

### 5.5 TECHNICALLY COMPLETE AND SETTLE PRODUCTION ORDER

[Process for closing orders and settling costs...]

---

## APPENDICES

### Appendix A: Quick Reference Cards

**Run MRP - Quick Steps:**
1. Open MRP application
2. Select plant and scope
3. Run MRP
4. Review results and exceptions
5. Convert planned orders
6. Monitor PRs

**Create Production Order - Quick Steps:**
1. Enter material and quantity
2. System explodes BOM
3. Schedule order
4. Check material availability
5. Save order
6. Release when ready

**Confirm Production Order - Quick Steps:**
1. Enter production order number
2. Enter yield quantity
3. Enter scrap (if any)
4. Enter actual time
5. Post confirmation
6. System posts goods receipt

### Appendix B: Common Applications

| **Application** | **Purpose** | **When to Use** |
|-----------------|-------------|-----------------|
| Maintain BOM | Create/change BOMs | New product or changes |
| Maintain Routing | Define production steps | New process or changes |
| Single-Item MRP | Plan one material | Urgent planning needed |
| Collective MRP Run | Plan all materials | Daily planning run |
| Create Production Order | Make production order | Convert planned order |
| Confirm Production Order | Record production | Output completed |

### Appendix C: Tips and Tricks

**MRP Tips:**
- Run at consistent times daily
- Process exceptions immediately
- Keep master data current
- Coordinate with Purchasing

**Production Order Tips:**
- Check component availability before release
- Print shop papers immediately after release
- Confirm orders same day as production
- Close completed orders promptly

### Appendix D: Frequently Asked Questions

**Q: How often should I run MRP?**
A: Minimum once daily. High-volume operations may run multiple times per day or even hourly.

**Q: What's the difference between planned order and production order?**
A: Planned order is MRP's proposal (not firm). Production order is firm commitment that reserves materials and goes to shop floor.

**Q: Can I change a production order after it's released?**
A: Yes, but changes are limited. You can adjust quantities and dates. Changing BOM requires special handling.

**Q: Why are my planned orders all showing late dates?**
A: Check lead times in material master. If lead times are too long, MRP schedules late. Also check component availability.

### Appendix E: Support Contacts

**For SAP Technical Issues:**
- IT Help Desk: helpdesk@homecontrol.com

**For Process Questions:**
- Production Planning Manager: [Contact]
- MRP Controller Lead: [Contact]
- Production Supervisor: [Contact]

---

**Document Revision History**

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | January 2025 | Training Development Team | Initial Production Planning Training Manual |

---

*End of Production Planning Training Manual*

