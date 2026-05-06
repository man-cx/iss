# Purchasing & Materials Management Training Manual
## SAP S/4HANA Implementation - Home Control

---

### Document Information
- **Department:** Purchasing & Materials Management
- **Version:** 1.0
- **Date:** January 2025
- **Target Audience:** Purchasing staff, Buyers, Commodity Managers, MRP Controllers, Master Data Team
- **Prerequisites:** Basic computer skills and familiarity with purchasing and materials management operations

---

### How to Use This Manual

This training manual is organized by business process. Each process contains:

1. **Process Overview** - Explains what the process does and why it's important
2. **When to Use** - Describes situations when you'll perform this process
3. **Roles Involved** - Lists who performs this process
4. **Step-by-Step Instructions** - Detailed walkthrough of how to complete the process
5. **Tips and Best Practices** - Helpful hints for efficient processing
6. **Common Issues and Solutions** - Troubleshooting guide
7. **Quick Reference** - Summary of key information

---

### Table of Contents

1. Introduction to Purchasing & MM in SAP
   - 1.1 Overview of SAP S/4HANA
   - 1.2 How Purchasing & MM Uses SAP
   - 1.3 Key Benefits

2. Getting Started
   - 2.1 Logging into SAP
   - 2.2 Navigating the SAP Interface
   - 2.3 Finding Applications
   - 2.4 Basic Functions

3. Master Data Processes
   - 3.1 Maintain Material Master
   - 3.2 Maintain Business Partner - Supplier Master
   - 3.3 Create Purchasing Info Record and Source List
   - 3.4 Maintain Quota Arrangement

4. Procurement Processes
   - 4.1 Procurement of Direct Materials (BOM Items)
   - 4.2 Procurement of Indirect Materials
   - 4.3 External Subcontracting
   - 4.4 Return to Vendor
   - 4.5 Stock Transfer Order

5. Material Requirements Planning
   - 5.1 Run MRP (Material Requirements Planning)
   - 5.2 Evaluate MRP Results
   - 5.3 Process MRP Exception Messages

6. Appendices
   - A. Quick Reference Cards
   - B. Common Applications
   - C. Material Status Codes
   - D. Supplier Groups
   - E. Tips and Tricks
   - F. Frequently Asked Questions
   - G. Support Contacts

---

## SECTION 1: INTRODUCTION TO PURCHASING & MM IN SAP

### 1.1 Overview of SAP S/4HANA

**What is SAP S/4HANA?**

SAP S/4HANA is Home Control's new enterprise resource planning (ERP) system that integrates all business processes across the company into one unified system.

**Key Features:**
- Real-time inventory visibility across all locations
- Automated material requirements planning
- Integrated supplier management
- Streamlined procurement workflows
- Electronic purchase orders and approvals
- Real-time spend analytics

### 1.2 How Purchasing & MM Uses SAP

The Purchasing and Materials Management department uses SAP to manage the complete procure-to-pay cycle, from material planning through supplier payments. SAP integrates purchasing with production, warehouse, finance, and quality management.

**Key Modules Used:**
- **MM (Materials Management)** - Material Master, Supplier Master, Purchase Requisitions, Purchase Orders, Goods Receipt, Invoice Verification
- **IM (Inventory Management)** - Stock management, physical inventory
- **PP-MRP** - Material Requirements Planning

**Integration with Other Departments:**
- **Finance**: Purchase orders create commitments; goods receipts and invoices update inventory values and accounts payable
- **Production**: Material requirements from production orders drive purchasing
- **Warehouse**: Goods receipts update inventory quantities and values
- **Sales**: Customer orders create demand that flows into MRP
- **Quality**: Quality inspection blocks or releases purchased materials

### 1.3 Key Benefits

**For Purchasing & MM Department:**
- Automated generation of purchase requisitions from MRP
- Real-time visibility of supplier performance
- Streamlined approval workflows
- Better control over purchasing spend
- Reduced manual data entry
- Integrated supplier information (prices, lead times, quality ratings)
- Easy tracking of purchase order status

**For Home Control:**
- Reduced inventory carrying costs through better planning
- Improved supplier relationships and negotiations
- Better visibility into procurement spending
- Faster procurement cycles
- Reduced stockouts and production delays
- Compliance with purchasing policies and approval limits

---

## SECTION 2: GETTING STARTED

### 2.1 Logging into SAP

**Step-by-Step Instructions:**

1. Open your web browser (Chrome or Edge recommended)
2. Navigate to the SAP login page: [Company URL]
3. Enter your User ID
4. Enter your Password
5. Click "Log On"

**✏️ Note:** Your User ID and initial password will be provided by IT. You will be prompted to change your password on first login.

**⚠️ Important:** Never share your SAP password. Each user must have their own login for audit and security.

### 2.2 Navigating the SAP Interface

**SAP Fiori Launchpad:**

The SAP Fiori Launchpad is your home screen. It contains tiles for all purchasing and materials management applications.

**Key Areas:**
- **Top Bar:** User settings, notifications, help
- **Tile Area:** Applications organized by groups (Purchasing, Materials Management, Master Data)
- **Search Bar:** Quickly find applications

**📸 Screenshot:** SAP Fiori Launchpad with Purchasing tiles

### 2.3 Finding Applications

**Method 1: Using Tiles**
- Locate the application tile on your home screen
- Click the tile to open

**Method 2: Using Search**
- Click search icon (🔍)
- Type application name
- Click from results

**Method 3: Using Menu**
- Click menu icon (☰)
- Browse application groups
- Click application name

**💡 TIP:**
> Bookmark your most-used applications by clicking the star icon. They'll appear in your "Favorites" group.

### 2.4 Basic Functions

**Common Buttons:**
- **Save** 💾 - Saves your work
- **Create** ➕ - Creates new document
- **Change** ✏️ - Opens in edit mode
- **Display** 👁 - Opens in view-only mode
- **Check** ✓ - Validates entries
- **Release** - Releases PR or PO for processing

**Keyboard Shortcuts:**
- `Ctrl + S` - Save
- `Ctrl + F` - Find
- `F3` - Back
- `Enter` - Continue/Execute

---

## SECTION 3: MASTER DATA PROCESSES

### 3.1 MAINTAIN MATERIAL MASTER

#### Process Overview

**Purpose:**
This process creates and maintains material master records, which contain all information about materials used at Home Control. Material masters include finished goods (FG), raw materials, components, packaging materials, and trading goods.

**Business Value:**
Material masters are the foundation of procurement, production, inventory management, and sales. Accurate material data ensures correct ordering, proper inventory valuation, and smooth production planning.

**Frequency:**
Daily - New materials are created regularly as new products are designed or new components are sourced.

#### When to Use This Process

You will perform this process when:
- R&D designs a new finished product
- Engineering identifies a new raw material or component
- Purchasing sources a new supplier for existing materials
- Material information needs to be updated (price, lead time, descriptions)
- Materials need to be extended to new plants or storage locations

**Example Scenario:**
R&D develops a new remote control model (FG material). You need to create the material master in SAP including basic data, purchasing data, MRP parameters, accounting data, and sales data so it can be procured, manufactured, and sold.

#### Who Performs This Process

**Primary Roles:**
- **Master Data Team** - Maintains most material master views
- **Project Team** - Requests FG material creation
- **R&D** - Creates raw material requests and maintains technical data
- **Purchasing** - Maintains purchasing and MRP data
- **Finance** - Runs costing and maintains financial views

#### Prerequisites

Before starting this process, ensure you have:
- ✓ Material number from Smart-Fulfillment System (for FG) or internal number assignment
- ✓ Material description (English and Chinese)
- ✓ Material type (FG, raw material, semi-finished, packaging, etc.)
- ✓ Base unit of measure (EA, KG, M, etc.)
- ✓ Material group assignment
- ✓ Purchasing information (lead time, supplier, price)
- ✓ Storage requirements (temperature controlled, hazardous, etc.)

**Required Information:**
- Material Type: FERT (Finished Goods), ROH (Raw Material), HALB (Semi-Finished)
- Material Group: Product category classification
- Base Unit: EA (Each), PC (Piece), KG (Kilogram), M (Meter)
- Plant and Storage Location
- MRP Type: PD (MRP), ND (No Planning), VB (Consumption-based)

#### SAP Application

**Application Name:** Manage Product Master Data

**How to Access:**
- From Fiori Launchpad, click "Manage Product Master Data" tile in "Master Data" group
- OR search for "Manage Product Master Data"

---

#### Step-by-Step Instructions for Finished Goods (FG)

#### Step 1: Request FG Material Creation

**What to do:**
Project Team submits request for new finished goods material.

**Procedure:**
1. Project Team identifies need for new FG material
2. Log into Smart-Fulfillment System (external system)
3. Apply for external material number
4. Enter material basic information:
   - Product name/description
   - Product category
   - Basic specifications
5. Submit request in Smart-Fulfillment System
6. System generates material number (external numbering)
7. Smart-Fulfillment System automatically calls SAP interface
8. Material master is created in SAP with basic data and classification
9. Material status automatically set to **ZA (Created)**

**📸 Screenshot:** Smart-Fulfillment System material request screen

**✏️ Note:** The interface between Smart-Fulfillment and SAP is automatic. The material appears in SAP within minutes of creation in Smart-Fulfillment.

---

#### Step 2: Maintain Additional Material Master Views (Master Data Team)

**What to do:**
Master Data Team completes the material master by adding MRP, Procurement, Finance, and Sales views.

**Procedure:**
1. Open **Manage Product Master Data** in SAP
2. Search for the newly created material by number or description
3. Click on material to open
4. Click "Change" to edit

**MRP View:**
5. Navigate to MRP tab
6. Enter the following:
   - **MRP Type**: PD (MRP) for planned materials
   - **Lot Size**: Lot-for-lot or Fixed lot size
   - **Procurement Type**: E (In-house production) or F (External procurement)
   - **Safety Stock**: Minimum stock level
   - **Reorder Point**: When to trigger replenishment
   - **Planned Delivery Time**: Lead time in days
   - **MRP Controller**: Person responsible for this material
7. Save MRP view

**Finance View:**
8. Navigate to Accounting tab
9. Enter:
   - **Valuation Class**: Links to GL accounts for inventory posting
   - **Price Control**: S (Standard price) or V (Moving average)
   - **Standard Price**: If using standard price control
   - **Price Unit**: Usually 1
10. Save Accounting view

**Procurement View:**
11. Navigate to Purchasing tab
12. Enter:
   - **Purchasing Group**: Buyer responsible
   - **Plant**: Manufacturing plant (e.g., CN13, CN17)
   - **Purchasing Value Key**: Standard time parameters
   - **Over-delivery Tolerance**: Percentage allowed
   - **Under-delivery Tolerance**: Percentage allowed
13. Save Purchasing view

**Sales View (for FG and kitting materials):**
14. Navigate to Sales tab
15. Enter:
   - **Sales Organization**: Sales area (e.g., SG21, CN13)
   - **Distribution Channel**: Distribution method
   - **Division**: Product line
   - **Item Category Group**: Controls order processing
   - **Availability Check**: ATP (Available-to-Promise) check rule
16. Save Sales view

17. After all views completed, change material status to **ZB (Pending Purchasing)**

**📸 Screenshot:** Material master with multiple tabs showing different views

**🔍 Key Fields Explained:**
- **MRP Type PD**: System calculates requirements and creates planned orders/requisitions automatically
- **Procurement Type E**: Material is produced in-house (has BOM and routing)
- **Procurement Type F**: Material is purchased from external suppliers
- **Valuation Class**: Links material to specific GL accounts (raw materials use different accounts than finished goods)

---

#### Step 3: Create Purchasing Info Record (If Needed)

**What to do:**
If this material will be purchased from suppliers, create purchasing info records with supplier information and pricing.

**Procedure:**
1. This process is covered in detail in Section 3.3
2. Buyer creates info record linking material to supplier(s)
3. Enter supplier price and lead time
4. Set validity dates
5. Mark as preferred supplier if applicable
6. After info record created, material status can progress to **ZC (Pending Costing)**

**✏️ Note:** For purely purchased materials, info record is essential. For manufactured items, it may not be needed.

---

#### Step 4: Run Material Costing (Finance)

**What to do:**
Finance runs standard cost calculation to establish the material's standard cost.

**Procedure:**
1. Finance department performs cost calculation
2. Uses costing variant and BOM (if manufactured item)
3. System calculates material cost based on:
   - Component costs (from BOM)
   - Activity costs (from routing)
   - Overhead costs
4. Standard cost is saved to material master
5. Material status changed to **ZD (Released)**
6. Material is now fully active and can be used in all transactions

**✅ Expected Result:** Material status = ZD, material can be purchased, produced, and sold

---

#### Step-by-Step Instructions for Raw Materials

#### Step 1: Request Raw Material Creation (R&D)

**What to do:**
R&D identifies need for new raw material and submits creation request.

**Procedure:**
1. R&D identifies new component or raw material needed
2. Log into Smart-Fulfillment System
3. Request internal material number assignment
4. System assigns number from internal range
5. R&D maintains classification and basic technical data
6. Set default values for Finance view
7. Material status set to **ZA (Created)**

---

#### Step 2: Maintain Purchasing and MRP Data (Purchasing)

**What to do:**
Purchasing maintains procurement-specific information.

**Procedure:**
1. Open **Manage Product Master Data**
2. Search for new raw material
3. Click "Change"
4. Navigate to MRP tab:
   - **MRP Type**: PD (for automatic planning)
   - **Procurement Type**: F (External procurement)
   - **Lot Size**: Based on supplier MOQ
   - **Safety Stock**: Buffer stock quantity
   - **Planned Delivery Time**: Supplier lead time
5. Navigate to Purchasing tab:
   - **Purchasing Group**: Assigned buyer
   - **Standard Price**: Current price (if known)
   - **Order Unit**: Unit supplier uses (EA, KG, etc.)
6. Save changes
7. Material status changed to **ZB (Pending Purchasing)**

---

#### Step 3: Extend to Sales View (If Kitting Material)

**What to do:**
For materials sold as spare parts or kits, Master Data Team adds sales view.

**Procedure:**
1. Open material in **Manage Product Master Data**
2. Click "Change"
3. Navigate to Sales tab
4. Enter sales organization, distribution channel, division
5. Enter sales-specific data (item category, tax classification)
6. Save
7. Material can now be sold to customers

**✏️ Note:** Most raw materials don't need sales view, only those sold as spare parts.

---

#### Step 4: Create Info Record (Purchasing)

**What to do:**
Link material to supplier(s) with pricing information.

**Procedure:**
1. Follow process in Section 3.3 to create purchasing info record
2. After info record created, proceed to costing

---

#### Step 5: Run Costing or Mark as No Costing

**What to do:**
Finance determines if material requires standard costing.

**Procedure:**
- **If costing needed**: Finance runs cost calculation, material status → **ZD (Released)**
- **If no costing needed**: Master Data Team changes status to **ZN (No Costing)**
- Material is now active for transactions

---

### Material Status Codes (Reference)

| **Status Code** | **Description** | **Can Be Used?** |
|-----------------|-----------------|------------------|
| ZA | Created | No - Incomplete data |
| ZB | Pending Purchasing | No - Awaiting purchasing data |
| ZC | Pending Costing | No - Awaiting cost calculation |
| ZD | Released | Yes - Fully active |
| ZL | LT Line Item | Special use |
| ZN | No Costing | Yes - Active without standard cost |
| ZT | FOC Gd Rcpt | Special use |
| ZW | No Recommend | Use with caution |
| ZZ | Phase-out | Being discontinued |

---

### Verification

**How to verify the process completed successfully:**
1. Search for material in **Manage Product Master Data**
2. Open material in display mode
3. Verify all required tabs have data (Basic, MRP, Purchasing, Accounting, Sales)
4. Check material status is **ZD (Released)** or **ZN (No Costing)**
5. Attempt to create purchase requisition or sales order (should work without errors)

**Success Indicators:**
- ✓ Material appears in search results
- ✓ All views properly maintained
- ✓ Material status is ZD or ZN
- ✓ Can be used in procurement and sales transactions

---

### Tips and Best Practices

💡 **Efficiency Tips:**
- Use "Copy from" function to create similar materials quickly
- Maintain a checklist of required fields for each material type
- Process materials in batches when creating multiple similar items
- Use material templates if your system supports them

💡 **Data Entry Tips:**
- Use clear, consistent descriptions (avoid abbreviations unless standard)
- Include both English and Chinese descriptions where applicable
- Be specific in material descriptions for easy identification
- Use proper units of measure (don't mix EA and PC randomly)

💡 **Things to Avoid:**
- ❌ Don't release materials (status ZD) before all data is complete
- ❌ Don't skip MRP parameters - they're critical for planning
- ❌ Don't use vague descriptions like "Part 1" or "Material ABC"
- ❌ Don't create duplicate materials - always search first
- ❌ Don't forget to extend to all relevant plants/storage locations

---

### Common Issues and Solutions

#### Issue 1: Material already exists error

**Symptom:** System says material number is already in use

**Cause:** Material was previously created or number is reserved

**Solution:**
1. Search for the material number in system
2. Check if existing material can be used
3. If not, request new material number from Smart-Fulfillment
4. If material was created but not completed, complete it instead of creating new

---

#### Issue 2: Cannot create purchase requisition for material

**Symptom:** When trying to create PR, material doesn't appear or gives error

**Cause:** Material status not released (ZD), or missing MRP/Purchasing data

**Solution:**
1. Check material status in master data
2. If status is ZA, ZB, or ZC, material is not ready
3. Contact Master Data Team to complete missing views
4. Verify MRP Type and Procurement Type are set correctly
5. Once status is ZD, try again

---

#### Issue 3: MRP not generating requirements for material

**Symptom:** MRP runs but doesn't create planned orders or PRs for this material

**Cause:** MRP Type set incorrectly or material not included in planning

**Solution:**
1. Open material master
2. Check MRP tab
3. Verify MRP Type = PD (not ND "No Planning")
4. Check if material has MRP Controller assigned
5. Verify plant is correct
6. Run MRP again for this material specifically

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Application Name | Manage Product Master Data |
| Frequency | Daily |
| Primary Roles | Master Data Team, R&D, Purchasing, Finance |
| Processing Time | 30-60 minutes per material (full cycle) |
| Prerequisites | Material number, basic data, purchasing info |

**Material Types:**
- **FERT**: Finished Goods (products we sell)
- **ROH**: Raw Materials (components we buy)
- **HALB**: Semi-Finished Goods (intermediate products)
- **HAWA**: Trading Goods (buy and resell)

**Critical Fields:**
- Material Number
- Material Type
- Base Unit of Measure
- MRP Type (PD for planning)
- Procurement Type (E=Make, F=Buy)
- Material Status (ZD=Active)

---

### 3.2 MAINTAIN BUSINESS PARTNER - SUPPLIER MASTER

#### Process Overview

**Purpose:**
This process creates and maintains supplier master records containing all information about vendors who supply materials to Home Control. Supplier masters include general data, company code data (accounting), and purchasing organization data.

**Business Value:**
Accurate supplier masters ensure proper payment processing, enable effective supplier performance tracking, support compliance with payment terms and tax regulations, and facilitate efficient procurement.

**Frequency:**
Weekly to monthly - New suppliers are added as business grows and new sourcing opportunities are identified.

#### When to Use This Process

You will perform this process when:
- Purchasing identifies a new supplier for materials or services
- Commodity Manager negotiates with new vendor
- Existing supplier information needs updating (address, bank details, payment terms)
- Supplier needs to be extended to additional company codes or purchasing organizations
- Supplier status needs changing (blocked, unblocked)

**Example Scenario:**
Commodity Manager identifies a new supplier in Vietnam for plastic components. The supplier offers competitive pricing and good quality. You need to create the supplier master in SAP including general data, payment terms, bank account for wire transfers, and purchasing organization assignment so buyers can create purchase orders.

#### Who Performs This Process

**Primary Roles:**
- **Requestor/Commodity Manager** - Collects supplier information
- **AP Admin** - Validates bank information and fills accounting data
- **Financial Controller** - Approves supplier creation
- **Purchasing Director/Site Manager** - Final approval
- **Master Data Team** - Creates/changes supplier master in system

#### Prerequisites

Before starting this process, ensure you have:
- ✓ Completed Supplier Application Form
- ✓ Supplier legal name and address
- ✓ Supplier tax identification number
- ✓ Bank account details (for electronic payments)
- ✓ Payment terms agreed with supplier
- ✓ Supplier contact information
- ✓ Required approvals

**Required Information:**
- Legal company name
- Address (street, city, country, postal code)
- Country and region
- Tax numbers (VAT number, tax ID)
- Bank details (bank name, account number, SWIFT/BIC code)
- Currency for payments
- Payment terms (e.g., Net 30 days)
- Purchasing organization
- Supplier group classification

#### SAP Application

**Application Name:** Maintain Business Partner / Manage Supplier Master Data

**How to Access:**
- From Fiori Launchpad, click "Manage Supplier Master Data" tile
- OR search for "Maintain Business Partner"

---

#### Step-by-Step Instructions

#### Step 1: Collect Supplier Information

**What to do:**
Requestor/Commodity Manager gathers complete supplier information including banking details.

**Procedure:**
1. Identify new supplier through sourcing activities
2. Request supplier to complete Supplier Information Form
3. Collect the following documents:
   - Business license or registration certificate
   - Tax registration certificate
   - Bank account verification letter (with bank stamp)
   - Contact information (email, phone, address)
4. Complete internal Supplier Application Form with:
   - Supplier name (legal entity name)
   - Address details
   - Contact persons
   - Bank account information
   - Tax identification numbers
   - Requested payment terms
   - Justification for adding this supplier
5. Verify all information is complete and accurate

**📸 Screenshot:** Supplier Application Form template

**🔍 Key Information to Collect:**
- **Legal Name**: Must match business license exactly
- **Bank Details**: Account number, bank name, SWIFT code, beneficiary name
- **Tax IDs**: Different countries have different requirements
- **Currency**: Which currency supplier wants to be paid in

**✏️ Note:** Bank details are critical for electronic payments. Errors here cause payment delays and additional work.

---

#### Step 2: Validate Bank Information (AP Admin)

**What to do:**
AP Admin verifies bank details are correct and valid for electronic fund transfers.

**Procedure:**
1. Receive Supplier Application Form from requestor
2. Review bank account information section
3. Verify bank key (bank code) exists in SAP:
   - Search for bank in SAP bank directory
   - If bank not found, create bank master first
4. Check SWIFT code is valid (8 or 11 characters)
5. Verify account number format is correct for that country
6. Confirm beneficiary name matches supplier legal name
7. If any discrepancies, contact requestor for clarification
8. Once validated, fill in accounting-specific data:
   - **Reconciliation Account**: GL account for AP posting
   - **Payment Terms**: Code for payment terms (e.g., Z030 = Net 30)
   - **Payment Methods**: Allowed payment types (bank transfer, check)
   - **House Bank**: Home Control's bank for payments
9. Sign approval on form

**📸 Screenshot:** Bank validation checklist

**⚠️ IMPORTANT:**
> Incorrect bank details can result in misdirected payments, which are very difficult to recover. Always verify carefully.

---

#### Step 3: Obtain Approvals

**What to do:**
Route the Supplier Application Form through the approval chain.

**Procedure:**
1. After AP Admin validates, send form to **Financial Controller** for approval
2. Financial Controller reviews:
   - Business justification
   - Accounting data accuracy
   - Compliance with company policies
3. Financial Controller signs and forwards to **Purchasing Director/Site Manager**
4. Purchasing Director/Site Manager reviews:
   - Strategic fit
   - Supplier capability
   - Contract terms
5. Purchasing Director approves or rejects
6. If approved, form goes to Master Data Team for creation
7. If rejected, requestor is notified with reasons

**✏️ Note:** Approval process typically takes 3-5 business days. Plan accordingly when timing is critical.

---

#### Step 4: Create Supplier Master (Master Data Team)

**What to do:**
Master Data Team creates the supplier record in SAP with all approved data.

**Procedure:**
1. Open **Manage Supplier Master Data** application
2. Click "Create" button
3. Select supplier group (determines number range):
   - **Z001**: BOM/NPR Vendor (external procurement, 7 digits)
   - **Z002**: Inter Company Vendor (4 digits)
   - **ZEMP**: Employee Vendor (5 digits)
   - **ZCPD**: One-Time Vendor (3 digits)
4. System assigns supplier number or enter manually based on group

**General Data Section:**
5. Enter the following:
   - **Name 1**: Supplier legal name (first line)
   - **Name 2**: Additional name info if needed
   - **Search Term**: Abbreviation for quick search
   - **Street**: Street address
   - **City**: City name
   - **Postal Code**: ZIP/postal code
   - **Country**: Country code (CN, SG, US, etc.)
   - **Region**: State/province if applicable
   - **Language**: EN (English) or ZH (Chinese)
6. In Communication tab:
   - **Telephone**: Contact phone number
   - **Email**: Supplier email address
   - **Contact Person**: Name of primary contact
7. Save general data

**📸 Screenshot:** Supplier general data entry screen

**Company Code Data Section:**
8. Click "Create Company Code Data"
9. Select company code (SG21, CN13, CN17, etc.)
10. Enter the following:
   - **Reconciliation Account**: AP control account (from AP Admin)
   - **Payment Terms**: Payment terms code
   - **Payment Methods**: Allowed methods (D=Domestic transfer, I=International, M=Manual)
11. In Payment Transactions tab:
   - **Bank Country**: Supplier's bank country
   - **Bank Key**: Bank code
   - **Bank Account**: Account number
   - **Account Holder**: Beneficiary name
   - **IBAN**: If applicable (for European banks)
   - **SWIFT Code**: BIC/SWIFT code
12. In Correspondence tab:
   - **Currency**: Payment currency (SGD, CNY, USD, EUR)
13. Save company code data

**📸 Screenshot:** Company code data entry with bank details

**Purchasing Organization Data Section:**
14. Click "Create Purchasing Organization Data"
15. Select purchasing organization (e.g., SG21, CN13)
16. Enter:
   - **Purchasing Group**: Default buyer for this supplier
   - **Currency**: Ordering currency (may differ from payment currency)
   - **Terms of Payment**: Same as company code
   - **Minimum Order Value**: If applicable
   - **Order Currency**: Currency used in POs
17. In Purchasing Data tab:
   - **ABC Indicator**: A=Strategic, B=Important, C=Standard
   - **Goods Receipt-Based Invoice Verification**: Check if invoices auto-posted on GR
18. Save purchasing organization data

**📸 Screenshot:** Purchasing organization data screen

19. Verify all three levels (general, company code, purchasing org) are complete
20. Note the supplier number assigned

**🔍 Key Fields Explained:**
- **Reconciliation Account**: Links supplier to GL account for AP. Usually same for all suppliers in a company code.
- **Payment Terms**: Controls due date calculation. Z030 = Net 30 days.
- **Payment Methods**: Limits how this supplier can be paid. Most use bank transfer (D or I).
- **GR-Based IV**: If checked, invoice is automatically created when goods are received. Saves time for routine purchases.

---

#### Step 5: Test and Verify

**What to do:**
Verify the supplier master was created correctly and can be used in transactions.

**Procedure:**
1. Search for newly created supplier in **Manage Supplier Master Data**
2. Open supplier in display mode
3. Verify all data is correct:
   - General data (name, address)
   - Company code data (payment terms, bank details)
   - Purchasing organization data
4. Check supplier number was assigned correctly
5. Attempt to create a test purchase order (optional):
   - Open **Create Purchase Order**
   - Enter supplier number
   - Supplier name should auto-populate
   - Add a material line item
   - Save as draft (don't send to supplier)
6. If successful, supplier is ready for use

**✅ Expected Result:**
- Supplier appears in search results
- All three data levels are complete
- Supplier can be selected in purchase orders
- Bank details are accurate

---

#### Step 6: Communicate Completion

**What to do:**
Inform requestor and relevant teams that supplier is ready.

**Procedure:**
1. Send email to Commodity Manager/Requestor with:
   - Supplier number
   - Supplier name
   - Company codes where available
   - Purchasing organizations where available
2. Copy Purchasing Manager and AP Admin
3. Update supplier tracking log if applicable
4. File the approved Supplier Application Form

**✏️ Note:** Keep original documents for audit purposes (usually 7 years retention).

---

### Supplier Groups (Reference)

| **Supplier Group** | **Description** | **Number Range** | **Use Case** |
|--------------------|-----------------|------------------|--------------|
| Z001 | BOM/NPR Vendor | 7 digits | Regular suppliers of materials and services |
| Z002 | Inter Company | 4 digits | Other Home Control entities (internal trading) |
| ZEMP | Employee Vendor | 5 digits | Employees who need reimbursement or payments |
| ZCPD | One-Time Vendor | 3 digits | Suppliers used once or rarely (uses CPD account) |

---

### Verification

**How to verify the process completed successfully:**
1. Supplier appears in **Manage Supplier Master Data** search
2. All three data levels present (general, company code, purchasing org)
3. Bank details match Supplier Application Form
4. Supplier selectable in purchase order creation
5. No error messages when saving

**Success Indicators:**
- ✓ Supplier number assigned
- ✓ All required fields filled
- ✓ Bank details validated
- ✓ Approvals documented
- ✓ Can create PO to supplier

---

### Tips and Best Practices

💡 **Efficiency Tips:**
- Use "Copy from" to create similar suppliers quickly (e.g., multiple locations of same company)
- Maintain a supplier creation checklist to ensure nothing is missed
- Process supplier requests in batches weekly
- Keep digital copies of supplier documents in shared folder

💡 **Data Entry Tips:**
- Always use legal entity name, not trading name or abbreviation
- Double-check bank account numbers - read them back digit by digit
- Use consistent formatting for addresses (makes reports look professional)
- Include country code in phone numbers

💡 **Things to Avoid:**
- ❌ Don't create supplier without proper approvals
- ❌ Don't skip bank validation - payment errors are costly
- ❌ Don't use internal nicknames for supplier names
- ❌ Don't create duplicate suppliers - always search first
- ❌ Don't forget to extend to all needed company codes and purchasing orgs

---

### Common Issues and Solutions

#### Issue 1: Bank key not found in system

**Symptom:** When entering bank details, system says bank key doesn't exist

**Cause:** Bank is not in SAP bank directory yet

**Solution:**
1. You need to create bank master first
2. Go to **Manage Banks-Master Data** application
3. Click "Create"
4. Enter bank country and bank key (bank code)
5. Enter bank name and address
6. Enter SWIFT code
7. Save bank master
8. Return to supplier master and continue

---

#### Issue 2: Cannot create purchase order to new supplier

**Symptom:** Supplier number entered but system gives error or won't continue

**Cause:** Supplier not extended to purchasing organization, or purchasing data incomplete

**Solution:**
1. Open supplier master in change mode
2. Check if purchasing organization data exists
3. If missing, create purchasing organization data
4. Fill all required purchasing fields
5. Save and try PO again

---

#### Issue 3: Payment failed due to invalid bank details

**Symptom:** Payment run processed but payment to this supplier failed

**Cause:** Bank account number or SWIFT code incorrect

**Solution:**
1. Contact supplier to reconfirm bank details
2. Request bank verification letter with bank stamp
3. Open supplier master in change mode
4. Correct bank details in company code data
5. Save
6. Rerun payment for this supplier
7. Update original supplier form with corrected info

---

#### Issue 4: Wrong reconciliation account

**Symptom:** AP postings go to wrong GL account

**Cause:** Reconciliation account in supplier master is incorrect

**Solution:**
1. Check with AP Admin what correct account should be
2. Open supplier master in change mode
3. Navigate to company code data
4. Change reconciliation account to correct one
5. Save
6. Note: Past postings remain on old account; only new postings use new account
7. May need GL transfer posting to move old balances

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Application Name | Manage Supplier Master Data / Maintain Business Partner |
| Frequency | Weekly to Monthly |
| Primary Role | Master Data Team (with approvals from AP, Finance, Purchasing) |
| Processing Time | 30-45 minutes for full creation |
| Prerequisites | Completed application form, bank details, approvals |

**Supplier Groups:**
- **Z001**: Regular suppliers (BOM/NPR vendors)
- **Z002**: Intercompany (internal)
- **ZEMP**: Employees
- **ZCPD**: One-time suppliers

**Critical Fields:**
- Legal Name
- Address
- Bank Account Number
- SWIFT Code
- Payment Terms
- Reconciliation Account
- Purchasing Organization

**Common Payment Terms:**
- Z000: Due immediately
- Z030: Net 30 days
- Z045: Net 45 days
- Z060: Net 60 days

---

*[Continuing with remaining sections...]*

### 3.3 CREATE PURCHASING INFO RECORD AND SOURCE LIST

[Process details continue in same comprehensive format...]

### 3.4 MAINTAIN QUOTA ARRANGEMENT

[Process details continue...]

---

## SECTION 4: PROCUREMENT PROCESSES

### 4.1 PROCUREMENT OF DIRECT MATERIALS (BOM ITEMS)

[Detailed process instructions continue...]

### 4.2 PROCUREMENT OF INDIRECT MATERIALS

[Process details continue...]

---

## SECTION 5: MATERIAL REQUIREMENTS PLANNING

### 5.1 RUN MRP (MATERIAL REQUIREMENTS PLANNING)

[Detailed process instructions continue...]

---

## APPENDICES

### Appendix A: Quick Reference Cards

[Quick reference summaries...]

### Appendix B: Common Applications

| **Application Name** | **Purpose** | **Who Uses It** |
|----------------------|-------------|-----------------|
| Manage Product Master Data | Create/change materials | Master Data Team, R&D, Purchasing |
| Manage Supplier Master Data | Create/change suppliers | Master Data Team |
| Manage Purchasing Info Records | Maintain supplier prices | Purchasing, Buyers |
| Create Purchase Order | Order from suppliers | Buyers, Purchasing |
| Manage Purchase Requisitions | Review/convert PRs | Buyers |
| Single-Item, Multi-Level MRP | Run material planning | MRP Controller |

### Appendix C: Material Status Codes

(Already included above)

### Appendix D: Supplier Groups

(Already included above)

### Appendix E: Tips and Tricks

**Searching for Materials:**
- Use wildcards: * for multiple characters
- Search by description if you don't know number
- Use material group to narrow results

**Searching for Suppliers:**
- Use search term field for quick lookup
- Search by city if multiple suppliers
- Use partial name search

**Creating Purchase Orders:**
- Use "Copy from" to duplicate similar POs
- Save frequently used POs as templates
- Use collective PO for multiple requisitions

### Appendix F: Frequently Asked Questions

**Q: Can I delete a material master once created?**
A: No, materials cannot be deleted if any transactions exist. Mark as "phase-out" (ZZ status) instead.

**Q: What's the difference between info record and source list?**
A: Info record contains price and terms for material-supplier combination. Source list says which suppliers are approved for automatic procurement.

**Q: Why can't I create a PO for a material?**
A: Check material status (must be ZD or ZN), verify material has purchasing data maintained, ensure supplier is valid.

**Q: How long does MRP take to run?**
A: Depends on data volume. Single-item MRP: seconds to minutes. Full MRP run: 30-60 minutes.

### Appendix G: Support Contacts

**For SAP Technical Issues:**
- IT Help Desk: helpdesk@homecontrol.com
- Phone: +XX-XXXX-XXXX

**For Process Questions:**
- Purchasing Manager: [Name and contact]
- Master Data Team Lead: [Name and contact]
- MRP Controller: [Name and contact]

---

**Document Revision History**

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | January 2025 | Training Development Team | Initial Purchasing & MM Training Manual |

---

*End of Purchasing & Materials Management Training Manual*

