# SAP S/4HANA Implementation - Process and Role Analysis
## Home Control Company

---

## Document Purpose
This document provides a comprehensive analysis of all business processes, user roles, and workflows identified in the SAP S/4HANA implementation design documents. This analysis serves as the foundation for creating end-user training materials.

---

## 1. FINANCE DEPARTMENT

### 1.1 General Ledger (FI-GL) Processes

#### Process: Manage GL Master Records
**Purpose:** Create and maintain general ledger account master data at company code and chart of accounts level.

**Key Roles:**
- GL Administrator (local level)
- GL Administration - Central (global level)
- Finance Manager (GL Reporting)

**Business Process Steps:**
1. Business Unit requests new or changed GL accounts
2. GL administrator checks if account exists at company code level
3. If exists, inform requestor; if not, check at Chart of Accounts (COA) level
4. For new accounts at COA level, GL administrator prepares request form with business justification
5. Request reviewed and approved by management
6. GL Administration - central creates GL account at COA level
7. GL administrator extends account to company code level
8. Assign GL account to Financial Statement version
9. Inform Business Unit of completion

**Key Applications:**
- Manage G/L Account Master Data
- Display G/L Account Balances
- Display Line Items in General Ledger

---

#### Process: Manage Posting in GL and Parallel Ledger
**Purpose:** Record financial transactions in general ledger and parallel ledgers for different reporting requirements.

**Key Roles:**
- GL Processing Officer
- Finance Manager (GL Reporting)

**Business Process Steps:**
1. Finance receives supporting documents for GL postings
2. GL processing officer makes GL postings if documents are complete
3. Posting documents update G/L account balances
4. Finance Manager checks GL documents and postings
5. If errors found, Finance Manager notifies poster to reverse documents
6. Poster reverses documents if GL errors exist
7. If documents are correct, Finance Manager signs document list

**Key Applications:**
- Manage Journal Entries
- Display G/L Account Balances
- Display Line Items in General Ledger

---

#### Process: Month End Closing Operations
**Purpose:** Execute month-end closing activities to prepare financial statements.

**Key Roles:**
- GL Executive Periodic
- AA Executive Periodic (Asset Accounting)
- FI Treasury Officer
- Bank Admin

**Business Process Steps:**
1. List all GL Parked Documents and analyze
2. Run asset depreciation
3. Perform GR/IR Auto Clearing
4. Maintain Exchange rates (both M and ME rates)
5. Open MM posting period for next month
6. Open FI posting period (GL/AP/AR/Fixed Assets/Inventory)
7. Reconcile Bank Statement
8. GL Periodic Postings (recurring entries)
9. AR/AP/GL Adjustments
10. Open Item Clearing
11. Foreign Currency Revaluation
12. Close FI Posting Period (AP/AR/Fixed Assets/Inventory)
13. GL Adjustment
14. Close FI Posting Period for GL
15. Run reports

**Key Applications:**
- Schedule Asset Accounting Jobs
- Schedule General Ledger Jobs
- Currency Exchange Rates
- Close Periods
- Manage Posting Periods
- Clear Open Items
- Automatic Clearing
- Manage Journal Entries
- Manage Recurring Journal Entries

---

#### Process: Balance Carryforward
**Purpose:** Transfer year-end balances to new fiscal year.

**Key Roles:**
- GL Executive Periodic
- AA Executive Periodic

**Business Process Steps:**
1. Transfer P&L Accounts Balance to Retained Earning Account
2. Carry Forward Balance Sheet Items - GL Balances
3. Review Opening Balances in New Fiscal Year
4. Close previous asset fiscal year and open new Fiscal Year

**Key Applications:**
- Schedule General Ledger Jobs (Balance Carryforward template)
- Display G/L Account Balances
- Make Company Code Settings Asset Accounting-Specific

---

### 1.2 Accounts Payable (FI-AP) Processes

#### Process: Manage Invoice Processing without PO
**Purpose:** Process vendor invoices that are not related to purchase orders.

**Key Roles:**
- AP Processing Officer
- Finance Manager

**Business Process Steps:**
1. Receipt of invoice from vendors for non-PO/SO
2. Finance and/or end user signs on original invoices
3. Physical verification of invoices by Finance
4. (Singapore only) Invoices sent to Account Payable team in China
5. Finance Authorizer posts invoice without Purchase Order/Service Order in system

**Key Applications:**
- Create Incoming Invoices
- Supplier Line Items China

---

#### Process: Manage Vendor Payments
**Purpose:** Process payments to suppliers according to payment terms.

**Key Roles:**
- AP Processing Officer
- AP Admin
- Finance Manager (Reviewer and Approver)

**Business Process Steps:**
1. AP officer checks invoices approved and pending for payment
2. AP officer generates payment proposal
3. AP officer reviews and edits Proposal List & Exception List
4. Approval of payment proposal
5. Payment run executed
6. Payment documents posted
7. Generate payment files for bank
8. Download payment files
9. Upload payment files to bank portal

**Key Applications:**
- Process Payment Items for Invoices
- Supplier Line Items China
- Process Payments for Invoices

**Master Data:**
- House Banks
- Payment Methods (Internal transfer, Domestic, International, Manual)
- Payment Terms

---

#### Process: Manage Vendor Down Payment
**Purpose:** Process advance payments to suppliers.

**Key Roles:**
- AP Processing Officer

**Business Process Steps:**
1. Receive down payment request from supplier
2. Create down payment request in system
3. Process down payment using payment program
4. Clear down payment against final invoice

**Key Applications:**
- Create Incoming Invoices
- Process Payment Items for Invoices

---

### 1.3 Accounts Receivable (FI-AR) Processes

#### Process: Manage Customer Incoming Payments
**Purpose:** Process customer payments and clear open invoices.

**Key Roles:**
- AR Processing Officer
- AR Admin

**Business Process Steps:**
1. Receive customer payment notification
2. Post incoming payment
3. Clear payment against open invoices
4. Process automatic clearing with Electronic Bank Statement
5. Manually clear exceptions

**Key Applications:**
- Post Incoming Payments
- Clear Open Items
- Automatic Clearing

**Master Data:**
- Customer Master
- Payment Terms
- Tax Codes (Sales tax)
- Reconciliation Accounts

---

#### Process: Manage Customer Down Payment
**Purpose:** Process advance payments from customers.

**Key Roles:**
- AR Processing Officer

**Business Process Steps:**
1. Receive down payment from customer
2. Post down payment request
3. Clear down payment against final invoice

**Key Applications:**
- Post Incoming Payments
- Clear Open Items

---

### 1.4 Fixed Assets (FI-AA) Processes

#### Process: Manage Asset Master Data
**Purpose:** Create and maintain fixed asset master records.

**Key Roles:**
- Asset Admin
- Finance Manager

**Business Process Steps:**
1. Receive request for new asset master
2. Review and verify request
3. Create asset master with required data
4. Assign asset to cost center/profit center
5. Set depreciation parameters
6. Inform requester of completion

**Key Applications:**
- Manage Asset Master Data
- Display Asset Explorer

**Master Data:**
- Asset Classes
- Depreciation Keys
- Depreciation Areas

---

#### Process: Manage Capitalization of Assets
**Purpose:** Capitalize assets acquired through purchase orders.

**Key Roles:**
- Asset Admin
- AP Processing Officer

**Business Process Steps:**
1. Create asset master
2. Create purchase order with asset assignment
3. Receive goods receipt
4. Post invoice verification with asset reference
5. Asset automatically capitalized
6. Verify asset values

**Key Applications:**
- Manage Asset Master Data
- Display Asset Explorer
- Create Purchase Order

---

#### Process: Manage Sale of Asset
**Purpose:** Process disposal of assets through sale.

**Key Roles:**
- Asset Admin

**Business Process Steps:**
1. Determine asset to be sold
2. Post asset sale transaction
3. Calculate gain/loss on disposal
4. Update asset status

**Key Applications:**
- Post Asset Retirement
- Display Asset Explorer

---

#### Process: Manage Transfer of Asset
**Purpose:** Transfer assets between cost centers, profit centers, or company codes.

**Key Roles:**
- Asset Admin

**Business Process Steps:**
1. Identify asset to be transferred
2. Post asset transfer
3. Update cost center/profit center assignment
4. Verify transfer posting

**Key Applications:**
- Post Asset Transfer
- Display Asset Explorer

---

#### Process: Manage Scrapping of Asset
**Purpose:** Process disposal of assets with no sale value.

**Key Roles:**
- Asset Admin

**Business Process Steps:**
1. Identify asset to be scrapped
2. Post asset scrapping
3. Write off remaining book value
4. Update asset status

**Key Applications:**
- Post Asset Retirement
- Display Asset Explorer

---

#### Process: Manage Asset Impairments
**Purpose:** Record impairment losses on assets.

**Key Roles:**
- Asset Admin
- Finance Manager

**Business Process Steps:**
1. Identify impaired assets
2. Calculate impairment amount
3. Post impairment loss
4. Adjust depreciation going forward

**Key Applications:**
- Post Manual Depreciation
- Display Asset Explorer

---

### 1.5 Controlling (CO) Master Data Processes

#### Process: Maintain Cost Centers
**Purpose:** Create and maintain cost center master data for cost tracking.

**Key Roles:**
- CO Administrator
- Finance Manager

**Business Process Steps:**
1. Users raise request for new cost center
2. Users fill cost center creation form (Name, Description, Category, Hierarchy, Company Code, Profit Center, Functional Area)
3. CO Administrator verifies requirement based on posting needs
4. CO Administrator checks if cost center exists
5. If exists, inform users; if not, create cost center
6. Create cost center in system
7. Update cost center groups/hierarchy
8. Inform Business Unit of completion

**Key Applications:**
- Manage Cost Centers
- Manage Global Hierarchies (Cost Center Hierarchy)

**Naming Convention:**
- 1st-4th digits: Company code
- 5th-6th digits: Country code
- 7th digit: Functional area (1=Manufacturing, 2=Sales, 3=G&A, 5=R&D)

---

#### Process: Maintain Profit Centers
**Purpose:** Create and maintain profit center master data for profitability analysis.

**Key Roles:**
- CO Administrator

**Business Process Steps:**
1. Receive request for new profit center
2. Verify business justification
3. Create profit center master
4. Assign to profit center hierarchy
5. Inform requester

**Key Applications:**
- Manage Profit Centers
- Manage Global Hierarchies (Profit Center Hierarchy)

---

#### Process: Manage Cost Element Master
**Purpose:** Maintain cost elements for cost accounting.

**Key Roles:**
- CO Administrator

**Business Process Steps:**
1. Create primary cost elements (automatically from G/L accounts)
2. Create secondary cost elements for internal allocations
3. Assign cost element category
4. Map to cost element groups

**Key Applications:**
- Manage Cost Elements

---

#### Process: Project Management
**Purpose:** Create and manage projects for R&D and capital investments.

**Key Roles:**
- Project Controller
- Finance Manager

**Business Process Steps:**
1. Receive project request
2. Create project definition
3. Create WBS elements
4. Assign budget
5. Monitor project costs
6. Close project

**Key Applications:**
- Manage Projects
- Monitor Projects

---

## 2. PURCHASING & MATERIALS MANAGEMENT DEPARTMENT

### 2.1 MM Master Data Processes

#### Process: Maintain Material Master
**Purpose:** Create and maintain material master records for all materials.

**Key Roles:**
- Project Team (for FG materials)
- R&D (for raw materials)
- Master Data Team
- Purchasing
- Finance

**Business Process Steps:**

**For Finished Goods (FG):**
1. Project Team requests creation of FG material
2. FG/Mechanical parts apply for external material numbers in Smart-Fulfillment System
3. Smart-Fulfillment System calls material master data interface to create in SAP
4. Basic Data view and classification maintained with default values
5. Material status set to ZA (Created)
6. Master Data Team maintains MRP view, Finance views, Procurement views, Sales view
7. Material status set to ZB (Pending Purchasing)
8. If needed, maintain info record (see process 2.3)
9. Material status set to ZC (Pending Costing)
10. Finance runs costing of materials
11. Material status changed to ZD (Released)
12. Check material data in SAP

**For Raw Materials:**
1. R&D requests creation of raw material
2. Material uses internal number from Smart-Fulfillment System
3. R&D maintains classification and default values in Finance view
4. Material status set to ZA (Created)
5. Purchasing maintains MRP view, Price, Procurement view
6. Material status set to ZB (Pending Purchasing)
7. If kitting material, Master Data Team maintains Sales view
8. If info record needed, proceed to info record process
9. Otherwise, material status set to ZN (No Costing)
10. Verify data
11. Finance runs costing
12. Material status changed to ZD (Released)

**Key Applications:**
- Manage Product Master Data
- Export Master Data - Products
- Smart-Fulfillment System (external interface)

**Material Status:**
- ZA: Created
- ZB: Pending Purchasing
- ZC: Pending Costing
- ZD: Released
- ZL: LT Line Item
- ZN: No Costing
- ZT: FOC Gd Rcpt
- ZW: No recommend
- ZZ: Phase-out

---

#### Process: Maintain Business Partner - Supplier Master
**Purpose:** Create and maintain supplier master records.

**Key Roles:**
- Requestor/Commodity Manager
- AP Admin
- Financial Controller
- Purchasing Director/Site Manager
- Master Data Team

**Business Process Steps:**
1. Requestor/Commodity Manager collects supplier information including bank details
2. Fill in supplier application form
3. AP Admin validates bank key and fills accounting data
4. Financial Controller approves
5. Purchasing Director/Site Manager approves
6. Master Data Team creates or changes supplier master data
7. Inform requestor/commodity manager of completion

**Key Applications:**
- Maintain Business Partner
- Manage Business Partner Master Data
- Manage Supplier Master Data

**Supplier Groups:**
- Z001: BOM/NPR Vendor (external procurement, 7 digits)
- Z002: Inter Company Vendor (4 digits)
- ZEMP: Employee Vendor (5 digits)
- ZCPD: One-Time Vendor (3 digits)

---

#### Process: Create Purchasing Info Record and Source List
**Purpose:** Maintain purchasing information records and approved source lists for materials.

**Key Roles:**
- Purchasing
- Purchasing Manager
- Purchasing Admin/SE (Sourcing Engineer)
- Commodity Manager

**Business Process Steps:**
1. Purchasing requests final quotation from vendor
2. Purchasing indicates create/change request in PPCA form (Price and Purchase Condition Agreement)
3. Submit PPCA Form
4. Check if material status is ZB (Pending Purchasing)
5. Determine if create or change info record
6. Purchasing Manager approves
7. If price change needed, Purchasing Manager reviews
8. Purchasing Manager approves price change
9. Determine if price rising or falling
10. If rising, Purchasing Manager approves
11. Purchasing Admin/SE changes price in info record OR changes other fields
12. Purchasing Admin/SE creates/updates info record & source list
13. Material status changed to ZC (Pending Costing)

**Key Applications:**
- Manage Purchasing Info Records
- Create Info Record
- Change Info Record
- Display Info Record
- Monitor Purchasing Info Record Price
- Manage Source Lists
- Maintain Source List

---

#### Process: Maintain Quota Arrangement
**Purpose:** Distribute procurement among multiple suppliers based on quotas.

**Key Roles:**
- Commodity Manager
- Purchasing Manager

**Business Process Steps:**
1. Commodity Manager/Purchasing Manager request final quotation from vendors
2. Create or change quota master data
3. Define quota percentages for each supplier
4. Set validity periods
5. Quota considered in MRP run

**Key Applications:**
- Manage Quota Arrangements

---

### 2.2 MM Procurement Processes

#### Process: Procurement of Direct Materials
**Purpose:** Procure BOM (Bill of Material) items for production.

**Key Roles:**
- MRP Controller
- Buyer
- Warehouse Staff

**Business Process Steps:**
1. MRP run generates planned orders and purchase requisitions
2. Buyer reviews and converts PR to PO
3. Buyer selects supplier from source list or quota arrangement
4. Send PO to supplier
5. Monitor PO delivery date
6. Receive goods at warehouse
7. Post goods receipt in SAP
8. Warehouse puts stock away
9. Invoice verification (may be automatic if goods receipt-based invoice verification)

**Key Applications:**
- Manage Purchase Requisitions
- Create Purchase Order
- Change Purchase Order
- Display Purchase Order
- Post Goods Receipt
- Enter Incoming Invoices

---

#### Process: Procurement of Indirect Materials
**Purpose:** Procure non-BOM items (office supplies, services, etc.).

**Key Roles:**
- Requestor
- Buyer
- Warehouse Staff (if applicable)

**Business Process Steps:**
1. Requestor creates purchase requisition for indirect material
2. PR routed for approval
3. Buyer reviews approved PR
4. Buyer creates purchase order
5. Send PO to supplier
6. Receive goods/service (if goods, post GR)
7. Post invoice

**Key Applications:**
- Create Purchase Requisition
- Manage Purchase Requisitions
- Create Purchase Order
- Post Goods Receipt (if applicable)
- Enter Incoming Invoices

---

#### Process: External Subcontracting
**Purpose:** Send materials to subcontractor for processing.

**Key Roles:**
- Buyer
- Warehouse Staff
- MRP Controller

**Business Process Steps:**
1. Create subcontracting purchase order with components
2. System reserves components for subcontracting
3. Issue components to subcontractor
4. Monitor subcontract order
5. Receive finished subcontract items
6. Post goods receipt
7. Components automatically consumed

**Key Applications:**
- Create Purchase Order (subcontracting type)
- Display Stock Overview
- Post Goods Receipt

---

#### Process: Return to Vendor
**Purpose:** Return defective or excess materials to supplier.

**Key Roles:**
- Warehouse Staff
- Buyer

**Business Process Steps:**
1. Identify materials to be returned
2. Create return delivery
3. Post goods issue for return
4. Create debit memo or credit request
5. Receive credit from supplier

**Key Applications:**
- Create Return Delivery
- Post Goods Issue
- Create Debit Memo Request

---

#### Process: Stock Transfer Order
**Purpose:** Transfer stock between plants or storage locations.

**Key Roles:**
- Planner
- Warehouse Staff

**Business Process Steps:**
1. Planner creates stock transfer order
2. Warehouse picks materials
3. Post goods issue at sending location
4. Transport materials
5. Post goods receipt at receiving location

**Key Applications:**
- Create Stock Transport Order
- Post Goods Issue
- Post Goods Receipt

---

### 2.3 MM Inventory Management Processes

#### Process: Core Inventory Management
**Purpose:** Manage stock movements and inventory balances.

**Key Roles:**
- Warehouse Staff
- Inventory Controller

**Business Process Steps:**
1. Perform goods movements (receipts, issues, transfers)
2. Monitor stock levels
3. Maintain stock overview
4. Manage serial numbers (if applicable)
5. Handle special stocks (subcontracting, consignment, etc.)

**Key Applications:**
- Post Goods Receipt
- Post Goods Issue
- Display Stock Overview
- Display Material Document

---

#### Process: Physical Inventory
**Purpose:** Count physical inventory and reconcile with system records.

**Key Roles:**
- Inventory Controller
- Warehouse Staff

**Business Process Steps:**
1. Create physical inventory document
2. Print count sheets
3. Perform physical count
4. Enter count results
5. Post inventory differences
6. Analyze variances

**Key Applications:**
- Create Physical Inventory Document
- Enter Physical Inventory Count
- Post Physical Inventory Difference
- Display Physical Inventory Document

---

## 3. WAREHOUSE & INVENTORY DEPARTMENT

### 3.1 Warehouse Processes

#### Process: Goods Receipt from Purchase Order
**Purpose:** Receive materials from suppliers into warehouse.

**Key Roles:**
- Warehouse Staff (Goods Receipt)
- Quality Inspector (if quality inspection required)

**Business Process Steps:**
1. Receive delivery from supplier
2. Check delivery against PO
3. Perform quality inspection (if required)
4. Post goods receipt in SAP with reference to PO
5. Print goods receipt label
6. Put away stock to storage location
7. System automatically updates inventory and posts to accounts

**Key Applications:**
- Display Purchase Orders for Goods Receipt
- Post Goods Receipt
- Display Material Document

---

#### Process: Goods Issue for Production
**Purpose:** Issue materials from warehouse to production.

**Key Roles:**
- Warehouse Staff (Goods Issue)
- Production Planner

**Business Process Steps:**
1. Receive request for material from production
2. Pick materials from storage location
3. Post goods issue with reference to production order or cost center
4. System reduces inventory and posts consumption

**Key Applications:**
- Display Production Order
- Post Goods Issue
- Display Material Document

---

#### Process: Stock Transfer Between Locations
**Purpose:** Move materials between storage locations within same plant.

**Key Roles:**
- Warehouse Staff

**Business Process Steps:**
1. Determine materials to be transferred
2. Post stock transfer in one step
3. Physically move materials
4. System updates stock quantities in both locations

**Key Applications:**
- Post Goods Movement
- Display Stock Overview

---

## 4. SALES DEPARTMENT

### 4.1 SD Master Data Processes

#### Process: Maintain Customer Master
**Purpose:** Create and maintain customer master records.

**Key Roles:**
- Sales Admin
- Credit Controller
- AR Admin

**Business Process Steps:**
1. Receive request for new customer
2. Collect customer information (general data, company code data, sales area data)
3. Credit Controller sets credit limit
4. Sales Admin creates customer master
5. Assign customer to sales area
6. Set pricing procedures and payment terms
7. Inform sales team

**Key Applications:**
- Maintain Business Partner
- Manage Customer Master Data

---

### 4.2 SD Sales Order Processing

#### Process: Create Sales Order
**Purpose:** Process customer orders for products.

**Key Roles:**
- Sales Order Processor
- Credit Controller

**Business Process Steps:**
1. Receive customer purchase order
2. Create sales order in SAP
3. Enter customer number, material, quantity, requested delivery date
4. System performs ATP (Available-to-Promise) check
5. System performs credit check
6. If credit ok, save sales order
7. System creates delivery requirements
8. Confirm order to customer

**Key Applications:**
- Create Sales Order
- Change Sales Order
- Display Sales Order
- Monitor Sales Orders

**Order Types:**
- Standard Order (OR)
- Sample Order
- FOC (Free of Charge)
- Kitting Order

---

#### Process: Rush Order Processing
**Purpose:** Process urgent customer orders with expedited handling.

**Key Roles:**
- Sales Order Processor
- Warehouse Staff
- Planner

**Business Process Steps:**
1. Receive urgent customer order
2. Create sales order with rush order type
3. Check stock availability immediately
4. If available, create delivery immediately
5. Pick, pack and ship same day
6. Post goods issue
7. Create billing document

**Key Applications:**
- Create Sales Order
- Create Outbound Delivery
- Post Goods Issue
- Create Billing Document

---

#### Process: Consignment Sales Order
**Purpose:** Process orders for consignment stock at customer location.

**Key Roles:**
- Sales Order Processor

**Business Process Steps:**
1. Create consignment fill-up order to send stock to customer
2. Post goods issue (stock moves to consignment at customer)
3. Customer uses consignment stock
4. Create consignment pick-up/issue order
5. Stock ownership transfers to customer
6. Create billing document

**Key Applications:**
- Create Sales Order (consignment types)
- Create Outbound Delivery
- Post Goods Issue
- Create Billing Document

---

#### Process: Sample Order Processing
**Purpose:** Process requests for product samples (no charge).

**Key Roles:**
- Sales Order Processor

**Business Process Steps:**
1. Receive sample request from customer
2. Create sample sales order (no pricing)
3. Create delivery
4. Pick and ship sample
5. Post goods issue
6. No billing document created

**Key Applications:**
- Create Sales Order (sample order type)
- Create Outbound Delivery
- Post Goods Issue

---

#### Process: Sales Order Change and Cancellation
**Purpose:** Modify or cancel existing sales orders.

**Key Roles:**
- Sales Order Processor
- Sales Manager (for approvals)

**Business Process Steps:**
1. Receive change request from customer
2. Check sales order status
3. If not yet delivered, make changes to order
4. If partially delivered, change remaining quantities
5. For cancellation, check if delivery created
6. If no delivery, delete order
7. If delivery exists, cancel delivery first then order
8. Inform customer of changes

**Key Applications:**
- Change Sales Order
- Display Sales Order
- Display Delivery

---

### 4.3 SD Delivery Processing

#### Process: Standard Delivery Processing
**Purpose:** Create and process outbound deliveries for customer orders.

**Key Roles:**
- Planner
- Warehouse Staff (Picker/Packer)

**Business Process Steps:**
1. Planner checks delivery due list based on shipping point
2. Create outbound delivery from sales order
3. System performs pick list creation
4. Warehouse picker picks materials based on pick list
5. Warehouse packer packs goods
6. Print delivery note and shipping labels
7. Goods loaded on truck
8. Post goods issue (PGI)
9. System updates inventory and creates billing document (if billing relevant)

**Key Applications:**
- Create Outbound Delivery
- Pick, Pack and Ship
- Display Deliveries
- Post Goods Issue

---

#### Process: Delivery Scheduling
**Purpose:** Schedule and monitor deliveries.

**Key Roles:**
- Planner
- Logistics Coordinator

**Business Process Steps:**
1. Monitor delivery due list
2. Check stock availability
3. Prioritize deliveries based on customer requirements
4. Create delivery schedule
5. Inform warehouse of picking requirements
6. Monitor delivery progress

**Key Applications:**
- Display Deliveries Due for Processing
- Monitor Outbound Deliveries
- Display Stock Overview

---

#### Process: Customer Return Processing
**Purpose:** Process returned goods from customers.

**Key Roles:**
- Sales Order Processor
- Warehouse Staff
- Quality Inspector

**Business Process Steps:**
1. Customer requests return authorization
2. Sales creates return sales order
3. System creates return delivery
4. Customer ships goods back
5. Warehouse receives goods
6. Quality inspector checks returned goods
7. Post goods receipt for return
8. Create credit memo for customer
9. Decide disposition of returned goods (restock, scrap, rework)

**Key Applications:**
- Create Sales Order (return type)
- Post Goods Receipt
- Create Credit Memo
- Post Stock Movement (if restocking or scrapping)

---

### 4.4 SD Billing Processing

#### Process: Standard Billing Processing
**Purpose:** Create invoices for customer shipments.

**Key Roles:**
- AR Admin
- Planner

**Business Process Steps:**
1. Planner completes delivery process and posts goods issue (PGI)
2. SAP system automatically generates customer billing documents
3. System creates accounting document in FI
4. Customer billing email triggered
5. AR Admin reviews billing documents
6. For China: AR Admin creates Golden Tax invoice in GTS
7. Print and send invoice to customer
8. Monitor customer payment

**Key Applications:**
- Manage Billing Documents
- Create Billing Document
- Display Billing Documents
- GTS (Golden Tax System for China)

---

#### Process: Collective Billing
**Purpose:** Create single invoice for multiple deliveries.

**Key Roles:**
- AR Admin

**Business Process Steps:**
1. Multiple deliveries completed for same customer
2. AR Admin selects deliveries for collective billing
3. Create collective billing document
4. System combines all deliveries into one invoice
5. Send invoice to customer

**Key Applications:**
- Create Collective Billing Document
- Manage Billing Documents

---

#### Process: Credit and Debit Memo Processing
**Purpose:** Create credit memos for returns or price adjustments; debit memos for additional charges.

**Key Roles:**
- Requester (Sales or Customer Service)
- AR Admin

**Business Process Steps:**
1. Receive credit/debit memo request
2. Create credit/debit memo sales order in SAP
3. Input price
4. AR Admin approves
5. Create credit/debit memo billing document
6. Send to customer

**Key Applications:**
- Create Sales Order (credit/debit memo types)
- Create Billing Document

---

#### Process: Golden Tax System Billing (China Only)
**Purpose:** Create official tax invoices in China's Golden Tax System.

**Key Roles:**
- AR Admin

**Business Process Steps:**
1. Complete standard billing process
2. AR Admin logs into GTS
3. Create Golden Tax invoice in SAP
4. System automatically creates invoice in GTS
5. Print official tax invoice
6. Send to customer

**Key Applications:**
- GTS (Golden Tax System)
- Create Billing Document

---

## 5. PRODUCTION PLANNING DEPARTMENT

### 5.1 PP Master Data Processes

#### Process: Maintain BOM (Bill of Material)
**Purpose:** Create and maintain product structures.

**Key Roles:**
- BOM Engineer (R&D)
- Master Data Team

**Business Process Steps:**
1. R&D designs product and determines components
2. BOM Engineer creates BOM in system
3. Enter header material
4. Add components with quantities
5. Define BOM usage (production, costing, etc.)
6. Set validity dates
7. Release BOM
8. Changes require version control

**Key Applications:**
- Maintain Bill of Material
- Display Bill of Material
- BOM Comparison

---

#### Process: Maintain Routing
**Purpose:** Define production process steps and work centers.

**Key Roles:**
- Process Engineer
- Production Planner

**Business Process Steps:**
1. Process Engineer defines production sequence
2. Create routing in system
3. Define operations
4. Assign work centers
5. Set standard values (setup time, run time, labor)
6. Release routing

**Key Applications:**
- Maintain Routing
- Display Routing

---

### 5.2 PP Planning Processes

#### Process: Demand and Material Requirements Planning (MRP)
**Purpose:** Calculate material requirements based on demand.

**Key Roles:**
- MRP Controller
- Production Planner

**Business Process Steps:**
1. MRP Controller schedules MRP run
2. System analyzes demand (sales orders, forecasts, stock requirements)
3. System checks available stock and scheduled receipts
4. System calculates net requirements
5. System creates planned orders for production
6. System creates purchase requisitions for purchased items
7. MRP Controller reviews exception messages
8. MRP Controller processes and resolves exceptions
9. Convert planned orders to production orders or purchase requisitions to POs

**Key Applications:**
- Single-Item, Multi-Level MRP
- Collective MRP Run
- Evaluating MRP Results
- Display Planning File Entries
- Display Stock/Requirements List

---

#### Process: Production Order Creation and Release
**Purpose:** Create and release production orders.

**Key Roles:**
- Production Planner

**Business Process Steps:**
1. Review planned orders from MRP
2. Convert planned order to production order
3. System explodes BOM to create material requirements
4. System determines routing operations
5. Production Planner schedules production order
6. Check material availability
7. Release production order
8. System reserves components
9. Print shop papers (production order, pick list)

**Key Applications:**
- Create Production Order
- Change Production Order
- Release Production Order
- Display Production Order

---

### 5.3 PP Execution Processes

#### Process: Goods Issue for Production Order
**Purpose:** Issue components from warehouse to production.

**Key Roles:**
- Warehouse Staff
- Production Supervisor

**Business Process Steps:**
1. Production order released
2. Warehouse receives pick list
3. Pick components from storage
4. Stage components at production line
5. Post goods issue with reference to production order
6. System reduces inventory and debits production order

**Key Applications:**
- Goods Issue for Order
- Display Material Document

---

#### Process: Confirmation of Production Order
**Purpose:** Record production output and time/activity confirmation.

**Key Roles:**
- Production Supervisor
- Production Operator

**Business Process Steps:**
1. Production completes operation
2. Production Supervisor confirms production order
3. Enter yield quantity (good quantity)
4. Enter scrap quantity (if applicable)
5. Enter actual time worked
6. System posts goods receipt for finished product
7. System relieves components
8. System calculates variances

**Key Applications:**
- Confirm Production Order
- Enter Time Ticket
- Post Goods Receipt

---

#### Process: Goods Receipt from Production
**Purpose:** Receive finished goods from production into warehouse.

**Key Roles:**
- Production Supervisor
- Warehouse Staff

**Business Process Steps:**
1. Production completes manufacturing
2. Post goods receipt for production order
3. Enter produced quantity
4. System increases finished goods inventory
5. System credits production order
6. Print finished goods label
7. Warehouse puts away finished goods

**Key Applications:**
- Goods Receipt for Order
- Display Material Document

---

#### Process: Production Order Settlement
**Purpose:** Settle production order costs to finished goods or variance accounts.

**Key Roles:**
- Cost Controller
- Production Planner

**Business Process Steps:**
1. All activities on production order completed
2. Technically complete production order (TECO)
3. Run production order settlement
4. System calculates actual costs
5. System compares to standard costs
6. System settles variances
7. Close production order

**Key Applications:**
- Technically Complete Production Order
- Settle Production Order
- Display Production Order Costs

---

## 6. CROSS-FUNCTIONAL PROCESSES

### 6.1 Document Management System (PP-DMS)

#### Process: Manage Product Documents
**Purpose:** Attach and manage technical documents to materials, BOMs, and orders.

**Key Roles:**
- Document Controller (R&D)
- BOM Engineer

**Business Process Steps:**
1. Create document info record
2. Attach document files (CAD drawings, specifications, etc.)
3. Link document to material master, BOM, or routing
4. Set document status
5. Control document versions
6. Release document

**Key Applications:**
- Create Document Info Record
- Change Document Info Record
- Display Document

---

## 7. KEY APPLICATIONS BY DEPARTMENT

### Finance Department Applications
- Manage G/L Account Master Data
- Manage Journal Entries
- Manage Recurring Journal Entries
- Create Incoming Invoices
- Process Payment Items for Invoices
- Post Incoming Payments
- Clear Open Items
- Manage Asset Master Data
- Post Asset Transactions
- Manage Cost Centers
- Manage Profit Centers
- Display Financial Reports
- Schedule General Ledger Jobs
- Manage Posting Periods

### Purchasing Department Applications
- Manage Product Master Data
- Manage Business Partner Master Data
- Manage Supplier Master Data
- Manage Purchasing Info Records
- Manage Source Lists
- Manage Quota Arrangements
- Create Purchase Requisition
- Manage Purchase Requisitions
- Create Purchase Order
- Change Purchase Order
- Display Purchase Order
- Monitor Purchase Orders

### Warehouse Department Applications
- Display Purchase Orders for Goods Receipt
- Post Goods Receipt
- Post Goods Issue
- Display Material Document
- Display Stock Overview
- Create Physical Inventory Document
- Enter Physical Inventory Count
- Post Goods Movement

### Sales Department Applications
- Manage Customer Master Data
- Create Sales Order
- Change Sales Order
- Display Sales Order
- Monitor Sales Orders
- Create Outbound Delivery
- Pick, Pack and Ship
- Display Deliveries
- Post Goods Issue
- Create Billing Document
- Manage Billing Documents
- Display Billing Documents

### Production Planning Department Applications
- Maintain Bill of Material
- Maintain Routing
- Single-Item, Multi-Level MRP
- Collective MRP Run
- Evaluating MRP Results
- Display Stock/Requirements List
- Create Production Order
- Change Production Order
- Release Production Order
- Confirm Production Order
- Goods Receipt for Order
- Goods Issue for Order
- Settle Production Order

---

## 8. INTEGRATION POINTS

### Finance ↔ Purchasing
- Purchase orders create commitments in FI
- Invoice verification posts to AP and cost accounts
- Payments reduce AP balances

### Finance ↔ Sales
- Sales orders create receivables commitments
- Billing documents create AR invoices
- Customer payments reduce AR balances

### Finance ↔ Production
- Production orders create WIP
- Goods receipts increase inventory value
- Order settlement posts variances

### Purchasing ↔ Warehouse
- Purchase orders drive goods receipts
- Goods receipts update inventory quantities and values

### Sales ↔ Warehouse
- Sales orders create delivery requirements
- Deliveries reduce inventory via goods issue

### Production ↔ Warehouse
- Production orders reserve components
- Goods issue to production reduces inventory
- Goods receipt from production increases inventory

### Production ↔ Planning
- MRP creates planned orders
- Planned orders convert to production orders
- Production orders drive material requirements

---

## Document Revision History
| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2025-01-XX | Training Development Team | Initial comprehensive process analysis |

---

*This document serves as the foundation for developing end-user training materials for all departments involved in the SAP S/4HANA implementation at Home Control.*

