**Core Inventory Management and Physical Inventory**

**核心库存管理和库存盘点**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****:** **HC_SAP_DD_MM07_Core Inventory Management and** **Physical Inventory**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Meos Xu                 MM Lead                08/08/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Rocky Cai            Project Manager        

      Jelly Ding              Purchasing          

     Yu Xiaodong              Purchasing          

      Cherry Qu               Purchasing          

     Xiaoqin Zhuo            Procurement          

      Lin Zhang              Procurement          

     Nancy Zhang                 SCM              

      Sara Wang                Planner            

      Irene Liu                Planner            

      Enly Teng               Logistics           

      Yining Xu        Master data maintenance    

      Sally Jin           Finance - AP/cash       

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [6](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [6](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [6](#design-document-approval-options)](#design-document-approval-options)

[2. Physical Inventory [6](#physical-inventory)](#physical-inventory)

[2.1 Purpose [6](#purpose)](#purpose)

[2.2 Business Reason [7](#business-reason)](#business-reason)

[2.3 Business Benefits [7](#business-benefits)](#business-benefits)

[2.4 Business Process [7](#business-process)](#business-process)

[▪ Business Process Steps [8](#business-process-steps)](#business-process-steps)

[2.5 HC Functional Requirements [9](#hc-functional-requirements)](#hc-functional-requirements)

[2.6 HC Delegation Of Authority [9](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[2.7 Standard Documents / Settings [9](#standard-documents-settings)](#standard-documents-settings)

[2.8 Design Considerations / Key Assumptions [9](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[2.9 Cross Functional Integration Dependencies [9](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[2.10 Support / Closing Considerations [9](#support-closing-considerations)](#support-closing-considerations)

[3. Post Goods Receipts [9](#post-goods-receipts)](#post-goods-receipts)

[3.1 Purpose [9](#purpose-1)](#purpose-1)

[3.2 Business Reason [9](#business-reason-1)](#business-reason-1)

[3.3 Business Benefits [10](#business-benefits-1)](#business-benefits-1)

[3.4 Business Process for Post Goods Receipts of BOM Materials [11](#business-process-for-post-goods-receipts-of-bom-materials)](#business-process-for-post-goods-receipts-of-bom-materials)

[▪ Business Process Steps [12](#business-process-steps-1)](#business-process-steps-1)

[3.5 Business Process for Post Goods Receipts of Indirect Purchasing [13](#business-process-for-post-goods-receipts-of-indirect-purchasing)](#business-process-for-post-goods-receipts-of-indirect-purchasing)

[▪ Business Process Steps [13](#business-process-steps-2)](#business-process-steps-2)

[3.6 HC Functional Requirements [14](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[3.7 HC Delegation Of Authority [14](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[3.8 Standard Documents / Settings [14](#standard-documents-settings-1)](#standard-documents-settings-1)

[3.9 Design Considerations / Key Assumptions [14](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[3.10 Cross Functional Integration Dependencies [14](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[3.11 Support / Closing Considerations [15](#support-closing-considerations-1)](#support-closing-considerations-1)

[4. Post Goods issue [15](#post-goods-issue)](#post-goods-issue)

[4.1 Purpose [15](#purpose-2)](#purpose-2)

[4.2 Business Reason [15](#business-reason-2)](#business-reason-2)

[4.3 Business Benefits [15](#business-benefits-2)](#business-benefits-2)

[4.4 SIV- Stock Issue Voucher [16](#siv--stock-issue-voucher)](#siv--stock-issue-voucher)

[4.5 Business Process for Post Goods issue for SIV [16](#business-process-for-post-goods-issue-for-siv)](#business-process-for-post-goods-issue-for-siv)

[▪ Business Process Steps [17](#business-process-steps-3)](#business-process-steps-3)

[4.6 HC Functional Requirements [17](#hc-functional-requirements-2)](#hc-functional-requirements-2)

[4.7 HC Delegation Of Authority [17](#hc-delegation-of-authority-2)](#hc-delegation-of-authority-2)

[4.8 Standard Documents / Settings [17](#standard-documents-settings-2)](#standard-documents-settings-2)

[4.9 Design Considerations / Key Assumptions [18](#design-considerations-key-assumptions-2)](#design-considerations-key-assumptions-2)

[4.10 Cross Functional Integration Dependencies [18](#cross-functional-integration-dependencies-2)](#cross-functional-integration-dependencies-2)

[4.11 Support / Closing Considerations [18](#support-closing-considerations-2)](#support-closing-considerations-2)

[5. Transfer Posting [18](#transfer-posting)](#transfer-posting)

[5.1 Purpose [18](#purpose-3)](#purpose-3)

[5.2 Business Reason [18](#business-reason-3)](#business-reason-3)

[5.3 Business Benefits [18](#business-benefits-3)](#business-benefits-3)

[5.4 Business Process for Transfer Posting [19](#business-process-for-transfer-posting)](#business-process-for-transfer-posting)

[▪ Business Process Steps [19](#business-process-steps-4)](#business-process-steps-4)

[5.5 HC Functional Requirements [20](#hc-functional-requirements-3)](#hc-functional-requirements-3)

[5.6 HC Delegation Of Authority [20](#hc-delegation-of-authority-3)](#hc-delegation-of-authority-3)

[5.7 Standard Documents / Settings [20](#standard-documents-settings-3)](#standard-documents-settings-3)

[5.8 Design Considerations / Key Assumptions [20](#design-considerations-key-assumptions-3)](#design-considerations-key-assumptions-3)

[5.9 Cross Functional Integration Dependencies [20](#cross-functional-integration-dependencies-3)](#cross-functional-integration-dependencies-3)

[5.10 Support / Closing Considerations [20](#support-closing-considerations-3)](#support-closing-considerations-3)

[6. Authorization Roles [21](#authorization-roles)](#authorization-roles)

[6.1 Authorization Roles [21](#authorization-roles-1)](#authorization-roles-1)

[7. Document Types and Document Flow [21](#document-types-and-document-flow)](#document-types-and-document-flow)

[8. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [21](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[8.1 Reports [21](#reports)](#reports)

[8.1.1 Standard Reports [21](#standard-reports)](#standard-reports)

[8.1.2 HC Requested Reports [21](#hc-requested-reports)](#hc-requested-reports)

[8.2 Interfaces [22](#interfaces)](#interfaces)

[8.3 Conversions [22](#conversions)](#conversions)

[8.4 Enhancements [23](#enhancements)](#enhancements)

[8.5 Forms [23](#forms)](#forms)

[8.6 Programs [23](#programs)](#programs)

[8.7 Workflows [23](#workflows)](#workflows)

[9. Legend for Process Flow [24](#legend-for-process-flow)](#legend-for-process-flow)

> **\**

**Document Version History**

+:-----------:+:-------------------------------------------:+:------------------:+
| **Version** | **Summary of Change**                       | **Effective Date** |
+-------------+---------------------------------------------+--------------------+
| 1.0         | Create the initial version of the document. | 08/08/2025         |
+-------------+---------------------------------------------+--------------------+
| 1.1         | Change owner of 2.4 and3.4 process.         | 08/15/2025         |
|             |                                             |                    |
|             | Change 4.4 process.                         |                    |
+-------------+---------------------------------------------+--------------------+
|             |                                             |                    |
+-------------+---------------------------------------------+--------------------+

# Guidelines {#guidelines .LS_Heading-1}

## Design Document Approval Overview {#design-document-approval-overview .LS_Heading-3}

The SAP Implementation Project Design Documents are the result of the Fit / Gap workshops.  All Project Design Documents must be reviewed and approved by the Home Control team to confirm we have captured the appropriate requirements as well as gaps, proposed solutions, and RICEFW objects​ from the workshops.

SAP Design Documents are living, breathing documents. As the SAP system is configured, tested, modified, and approved, the design documents may be updated to reflect the final design​.

ISS Team Leads create the original design documents​. Should Home Control decide to update the Design Documents, it is up to Home Control to perform the updates.

As we leave the Explore stage and enter the Realize stage, we ask for approval but understand that there may be open decisions or uncertainty in some areas.  Therefore, we provide the following approval options.

## Design Document Approval Options​ {#design-document-approval-options .LS_Heading-3}

> [Sign-Off Without Reservation​]{.underline}

- No issues or concerns​ at this point

> [Sign-Off with Reservation​]{.underline}

- Minor issues or concerns (3-5) that need to be finalized during Realize stage.

- Place Reservation(s) on the Issues Log, assign owner and due date, manage​ issue/concern.

> [Withhold Sign-Off - Major Decisions Unresolved​]{.underline}

- Major design issues that need to be resolved in order to move forward in Realize stage (e.g., Internal Orders vs. Project Systems​)

- Place on the Issues Log, assign owner and due date, manage​ issue

- Complete Key Design Decision document and escalate (PMO then Executive Sponsor)

If you have any items that may withhold signature it is your responsibility to escalate as soon as possible

# Physical Inventory {#physical-inventory .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

This scenario covers the annual inventory process to count the stock on hand.

The process begins with the generation of the required inventory count sheets. Materials can be blocked here for posting during the physical inventory. Once the inventory sheets are printed out, the actual physical inventory count is realized for the given materials. The count result is entered in the system and discrepancies in the system quantities are reviewed. The inventory may be recounted until final counts are accepted and inventory differences are posted.

## Business Reason {#business-reason .LS_Heading-3}

During the inventory count, all the materials being inventoried are counted and entered physically. The stocks are counted individually for the materials in the inventory document/record. The count results are written on the printout of the inventory document/record. The printout is then directed back to the person responsible, so that he or she can enter the count into the system and analyze it. The count is compared to the book inventory quantities and differences are identified for analysis and eventual clearing.

Upon completion of the inventory count:

- The quantities of the material in the specific storage location (in Inventory Management) are adjusted.

- When the inventory difference is posted, the system creates a material document that records the adjusted stock balances and an accounting document that contains the necessary account activities.

Counting physical inventory process includes but is not limited to the following scenarios.

NOTE: Movement reversals not shown; these are typically the standard movement type +1 (e.g., 101 reversal is 102, 161 reversal is 162, etc.):

  -----------------------------------------------------------------------------------------------------------
  **Movement Type**   **Description**                     **Usage at HC**
  ------------------- ----------------------------------- ---------------------------------------------------
  701                 Goods receipt, physical inventory   Movement for posting + differences on stock count

  702                 Goods issue, physical inventory     Movement for posting - differences on stock count
  -----------------------------------------------------------------------------------------------------------

## Business Benefits {#business-benefits .LS_Heading-3}

- Get a transparent view on the stocks currently available

- Process inventory adjustments efficiently

## Business Process {#business-process .LS_Heading-3}

In Home control, we conduct annual inventory counts and routine inventory counts. Annual inventory counts need to be carried out in the system, which is the content of this process. Routine inventory counts will not be processed in the system.

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Step**   **Step Name**                                      **Role**                    **SAP App Name**                      **Expected Results**
  ---------- -------------------------------------------------- --------------------------- ------------------------------------- ------------------------------------------------------------
  001        Fix a date for annual counting                     Finance Admin               Non-SAP                               Fix a date for annual counting

  002        Inform to clear stock in non-warehouse locations   Warehouse Admin / Planner   Non-SAP                               Inform to clear stock in non-warehouse locations

  003        Finance informs to stop the transaction by email   Finance Admin               Non-SAP                               Finance informs to stop the transaction by email

  004        Inform the launch physical Stock count             Finance Admin               Non-SAP                               Inform the launch physical Stock count

  005        Transfer discrepancy stock to Warehouse            Procurement Admin           MIGO                                  Transfer discrepancy stock to Warehouse

  006        Download materials inventory                       Procurement Admin           Stock - Multiple Materials            Download materials inventory

  007        Create Physical Inventory Documents                Procurement Admin           Create Physical Inventory Documents   Create Physical Inventory Documents

  008        Generate Physical Counting sheet                   Subcontractor               Non-SAP                               Generate Physical Counting sheet

  009        Circulate the counting sheet to operator           Subcontractor               Non-SAP                               Circulate the counting sheet to operator

  010        Counting the result                                Subcontractor               Non-SAP                               Counting the result

  011        Display the difference List                        Subcontractor               Non-SAP                               Display the difference List

  012        Variance Accepted?                                 Procurement Admin           Non-SAP                               

  013        Organize Recount                                   Subcontractor               Non-SAP                               Organize Recount

  014        Approved?                                          Finance Admin               Non-SAP                               

  015        Prepare inventory count list                       Procurement Admin           Non-SAP                               Procurement prepare doc for finance upload inventory count

  016        Upload inventory count                             Finance Admin               Manage Physical Inventory Count       Upload inventory count

  017        List all inventory difference                      Finance Admin               MI20                                  List all inventory difference

  018        Post Inventory Count Differences                   Finance Admin               Manage Physical Inventory Count       Post Inventory Count Differences
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- In Home control, we conduct annual inventory counts and routine inventory counts. Annual inventory counts need to be carried out in the system, which is the content of this process.

- Subcontractors should adjust their inventory when counting physical inventory.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Inventory adjustment for unrestricted-use, quality inspection and blocked stock will be supported.

- Inventory at Subcontractor (Stock at Vendor) locations with quantity tracking are managed in Inventory management at the plant level, Special Stock 'O'. Thus, inventory count will be conducted using Inventory management functionalities.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# Post Goods Receipts {#post-goods-receipts .LS_Heading-1}

3.  

<!-- -->

2.  

## Purpose {#purpose-1 .LS_Heading-3}

Good receipts can occur when inventory arrives from a vendor. The inventory quantity and value are increased as a result of a goods receipt transaction.

## Business Reason {#business-reason-1 .LS_Heading-3}

Materials are arrived or indirect purchasing are confirmed, and need to post goods receipt.

Post goods receipt process includes but is not limited to the following scenarios.

NOTE: Movement reversals not shown; these are typically the standard movement type +1 (e.g., 101 reversal is 102, 161 reversal is 162, etc.):

+-------------------+------------------------------------------------------+-------------------------------------+
| **Movement Type** | **Description**                                      | **Usage at HC**                     |
+:==================+:=====================================================+:====================================+
| 101               | Goods Receipt Purchase Order                         |                                     |
+-------------------+------------------------------------------------------+-------------------------------------+
| 511               | Goods Receipt for no-charge                          | For no-charge receipt of materials. |
|                   |                                                      |                                     |
| 512               |                                                      |                                     |
+-------------------+------------------------------------------------------+-------------------------------------+
| 657               | Goods Receipt for return sales orders to block stock |                                     |
+-------------------+------------------------------------------------------+-------------------------------------+

## Business Benefits {#business-benefits-1 .LS_Heading-3}

- Support process-related goods receipt postings

- Support legally required goods receipt postings

> 

##  {#section .LS_Heading-3}

## Business Process for Post Goods Receipts of BOM Materials {#business-process-for-post-goods-receipts-of-bom-materials .LS_Heading-3}

![](media/media/image3.emf)

##  {#section-1 .LS_Heading-3}

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Step**   **Step Name**                                                         **Role**                   **SAP App Name**      **Expected Results**
  ---------- --------------------------------------------------------------------- -------------------------- --------------------- ---------------------------------------------------------------------
  001        Receive Cargo from Vendor                                             Supplier/Subcontractor     Non-SAP               Receive Cargo from Vendor

  002        Warehouse count the quantity against delivery document                Supplier/Subcontractor     Non-SAP               Warehouse count the quantity against delivery document

  003        Is there any variance? (Decision)                                     Supplier/Subcontractor     Non-SAP               

  004        Is it from Local Vendor? (Decision)                                   Supplier/Subcontractor     Non-SAP               

  005        Purchasing / Procurement liaise with Oversea vendor                   Supplier/Subcontractor     Non-SAP               Purchasing / Procurement liaise with Oversea vendor

  006        Will vendor change the DO or invoice? (Decision)                      Supplier/Subcontractor     Non-SAP               

  007        Vendor replenish the variance quantity                                Supplier/Subcontractor     Non-SAP               Vendor replenish the variance quantity

  008        GR based on actual Quantity                                           Supplier/Subcontractor     Non-SAP               GR based on actual Quantity

  009        Purchasing / Procurement to follow up actual GR quantity in invoice   Procurement / Purchasing   Non-SAP               Purchasing / Procurement to follow up actual GR quantity in invoice

  010        Pull Stock to Warehouse                                               Supplier/Subcontractor     Non-SAP               Pull Stock to Warehouse

  011        If inspection required? (Decision)                                    Supplier/Subcontractor     Non-SAP               

  012        Perform Inspection Check                                              Supplier/Subcontractor     Non-SAP               Perform Inspection Check

  013        Inspection Passed? (Decision)                                         Supplier/Subcontractor     Non-SAP               

  014        HC_SAP_DD_MM04_Return to Vendor                                       Warehouse Admin            /                     

  015        Post Goods Receipts                                                   Warehouse Admin            MIGO/Custom BTP APP   Post Goods Receipts manually or mass upload

  016        Quota Arrangement Relevant? (Decision)                                Warehouse Admin            Non-SAP               

  017        HC_SAP_DD_MM07_04_Transfer Posting                                    Warehouse Admin            Non-SAP               
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Business Process for Post Goods Receipts of Indirect Purchasing {#business-process-for-post-goods-receipts-of-indirect-purchasing .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Step**   **Step Name**                                                          **Role**                                 **SAP App Name**                              **Expected Results**
  ---------- ---------------------------------------------------------------------- ---------------------------------------- --------------------------------------------- ----------------------------------------------------------------------
  001        Arrival of Equipment / Services is provided                            NPI Purchasing / Procurement Requestor   Non-SAP                                       Arrival of Equipment / Services is provided

  002        Requestor check against the quantity, quality with delivery document   NPI Purchasing / Procurement Requestor   Non-SAP                                       Requestor check against the quantity, quality with delivery document

  003        Acceptable? (Decision)                                                 NPI Purchasing / Procurement Requestor   Non-SAP                                       

  004        Return to vendor / Replacement                                         NPR Purchasing Officer                   Non-SAP                                       Return to vendor / Replacement

  005        Start Replacement Procedure                                            Vendor                                   Non-SAP                                       Start Replacement Procedure

  006        Vendor refuse to replace the corrected goods                           NPR Purchasing Officer                   Non-SAP                                       Vendor refuse to replace the corrected goods

  007        Mark Deletion Flag to PO                                               NPR Purchasing Officer                   ME22N/Manage Purchase Orders                  Mark Deletion Flag to PO

  008        Sign receive on the delivery doc                                       NPI Purchasing / Procurement Requestor   Non-SAP                                       Sign receive on the delivery doc

  009        Post Good Receipt with Invoice                                         Warehouse Admin                          MIGO/Custom BTP APP                           Post Good Receipt With Invoice

  009A       Confirm Service Received                                               NPI Purchasing / Procurement Requestor   Manage Service Entry Sheets - Lean Services   Confirm Service Received

             HC_SAP_DD_MM02_04_Invoice Verification                                 AP Admin                                 /                                             
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements-1 .LS_Heading-3}

- For no-charge materials, warehouse admin can post goods receipts and issues without purchase orders and with movement type:511&512.

- Need a custom program to mass upload the BOM goods receipts.

- The process of posting goods receipts for indirect purchasing is focus on services and fixed assets and AUC which need to post goods receipts in SAP.

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-1 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- Inventory adjustment for unrestricted-use, quality inspection and blocked stock will be supported.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-1 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-1 .LS_Heading-3}

- N/A

# Post Goods issue {#post-goods-issue .LS_Heading-1}

4.  

<!-- -->

3.  

## Purpose {#purpose-2 .LS_Heading-3}

A Goods issue occurs when inventory quantities are deducted from the system and posted against a cost object, such as an R&D Engineering order, customer sales order, an inventory scrap account. Goods issues may also be performed if you are moving inventory from one location to another within a company. The quantity and value of the inventory is reflected in the material and accounting documents created when a goods issue occurs.

## Business Reason {#business-reason-2 .LS_Heading-3}

Post goods issue process includes but is not limited to the following scenarios.

NOTE: Movement reversals not shown; these are typically the standard movement type +1 (e.g., 101 reversal is 102, 161 reversal is 162, etc.):

+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| **Movement Type**         | **Description**                                  | **Usage at HC**                                                                                          |
+:==========================+:=================================================+:=========================================================================================================+
| 201                       | Goods Issue to Cost Center                       | SIV charge to cost center, including sample, Rework, etc.                                                |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| 551                       | Good issue to scrap                              | Only use for DA/ DP (DA use quality cost center, DP use manufacture cost center)                         |
|                           |                                                  |                                                                                                          |
|                           |                                                  | Scrapping movement for damage and shelf expiry- USE THIS ONE                                             |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| 901(Custom Movement type) | Scrap obsolescence                               | Scrap application issued by procurement, say for example scrap of safety stock, buffer stock, PCAN, etc. |
|                           |                                                  |                                                                                                          |
|                           |                                                  | Scrapping movement for obsolescence no need cost center                                                  |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| 291                       | GI for cost center                               | For Goods Issue to cost center and project, FG in project stage.                                         |
|                           |                                                  |                                                                                                          |
|                           |                                                  | FG SIV for project stage (need project number)                                                           |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| 543                       | Goods issue of components for subcontract vendor | Adjustment or backflush out from \"o\"- Material provided to vendor Unrestricted stock                   |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| 702                       | Goods issue, physical inventory                  | Movement for posting - differences on stock count                                                        |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| 601                       | Goods issue to sales order                       |                                                                                                          |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+
| 903(Custom Movement type) | Consump. for pallet                              | Consumption for pallet                                                                                   |
+---------------------------+--------------------------------------------------+----------------------------------------------------------------------------------------------------------+

## Business Benefits {#business-benefits-2 .LS_Heading-3}

- Support process-related goods issue postings

- Support legally required goods issue postings

## SIV- Stock Issue Voucher {#siv--stock-issue-voucher .LS_Heading-3}

SIV means- Full name is Stock Issue Voucher- is a paper form which recording the internal consumption for bonded material. The quantity will be utilized to report to Custom Authority and Custom handbook should reflect this change with new number. Import duty is claimed based on this quantity.

## Business Process for Post Goods issue for SIV {#business-process-for-post-goods-issue-for-siv .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

  -----------------------------------------------------------------------------------------------------------------------------------------------------
  **Step**   **Step Name**                                         **Role**          **SAP App Name**             **Expected Results**
  ---------- ----------------------------------------------------- ----------------- ---------------------------- -------------------------------------
  001        Identify material to be issued                        Requester         Non-SAP                      Identify material to be issued

  002        Perform SIV Request                                   Requester         Non-SAP                      Perform SIV Request

  003        Is FG? （Decision）                                   Requester         Non-SAP                      Most FG need to create reservation.

  004        Create Reservation to Cost Center                     Planner           Manage Manual Reservations   Create Reservation to Cost Center

             HC_SAP_DD_PP02_02_MRP Run                             /                 /                            

             HC_SAP_DD_MM02_Procurement of Direct Materials        /                 /                            

             HC_SAP_DD_MM07_02_Post Good Receipt                   /                 /                            

  006        Consult with subc about the inventory                 Warehouse Admin   Non-SAP                      

  007        Has the material been found?                          Warehouse Admin   Non-SAP                      

  008        Adjust pick list                                      Warehouse Admin   Non-SAP                      

  009        Identify the root cause and do necessary adjustment   Warehouse Admin   Non-SAP                      

  010        Perform Physical Movement                             Warehouse Admin   MIGO                         
  -----------------------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements-2 .LS_Heading-3}

- Need a custom program to mass upload the non-sales orders goods issue.

For Home Control, goods issue has been applied to below business scenarios:

- Scrap : Scrap from WHS or Scrap storage location

- Finished Good SIV : which includes commercial sampling, quality replacement

- Damage on Production :

- Damage on Arrival

- Project Based Consumption(FG & Material)

- Vendor Return

- Rework

- Trail Run

- Internal Consumption

- Components SIV: Engineer sample

## HC Delegation Of Authority {#hc-delegation-of-authority-2 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-2 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-2 .LS_Heading-3}

- Inventory adjustment for unrestricted-use, quality inspection and blocked stock will be supported.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-2 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-2 .LS_Heading-3}

- N/A

# Transfer Posting {#transfer-posting .LS_Heading-1}

5.  

<!-- -->

4.  

## Purpose {#purpose-3 .LS_Heading-3}

Stock transfers are a mechanism to transfer inventory from one place within a company or plant and reflect the inventory in a different location. Examples of stock transfers include the movement of inventory from one material to another, one storage location to another.

## Business Reason {#business-reason-3 .LS_Heading-3}

Transfer posting process includes but is not limited to the following scenarios.

NOTE: Movement reversals not shown; these are typically the standard movement type +1 (e.g., 101 reversal is 102, 161 reversal is 162, etc.):

  ------------------------------------------------------------------------------------------------------------------------------------
  **Movement Type**   **Description**                                               **Usage at HC**
  ------------------- ------------------------------------------------------------- --------------------------------------------------
  301                 From transferring from Plant to Plant                         Refer to description

  309                 Change material No from one to another within plant           Say for example, Relabeling, Rework A to B, etc.

  311                 Movement from location to location-transaction within plant   Refer to description

  541                 From Location to Material provided to vendor                  Stock transfer from SL to \"O\"

  542                 From Material provided to vendor to any location              Stock transfer from \"O\" to SL
  ------------------------------------------------------------------------------------------------------------------------------------

## Business Benefits {#business-benefits-3 .LS_Heading-3}

- Support process-related transfer postings

- Support legally required transfer postings

## Business Process for Transfer Posting {#business-process-for-transfer-posting .LS_Heading-3}

## ![](media/media/image6.emf) {#section-2 .LS_Heading-3}

## Business Process Steps {#business-process-steps-4 .LS_Heading-3}

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Step**   **Step Name**                                                              **Role**          **SAP App Name**                 **Expected Results**
  ---------- -------------------------------------------------------------------------- ----------------- -------------------------------- --------------------------------------------------------------------------
  001        Is Material to Material?（Decision）                                       Warehouse Admin   Non-SAP                          

  002        Material transfer（Movement Type: 309）                                    Warehouse Admin   MIGO                             Material transfer Movement Type: 309）

  003        Physical Stock to be relabeled or relocation                               Warehouse Admin   Non-SAP                          Physical Stock to be relabeled or relocation

  004        Is a SL change? （Decision）                                               Warehouse Admin   Non-SAP                          

  005        Goods transfer between storage location (Movement Type: 311)               Warehouse Admin   MIGO/Transfer Stock - In-Plant   Goods transfer between storage location (Movement Type: 311）

  006        Move Stock from Source to Destination Location                             Warehouse Admin   Non-SAP                          Move Stock from Source to Destination Location

  007        Is Subcontract Stock Movement? （Decision）                                Warehouse Admin   Non-SAP                          

  008        Goods transfer Subc Location from storage. loc. (Movement Type: 541/542)   Warehouse Admin   MIGO                             Goods transfer Subc Location from storage loc. (Movement Type: 541/542)

  009        Transport Stock to CBET or reverse                                         Warehouse Admin   Non-SAP                          Transport Stock to CBET or reverse

  010        Is a Plant change? （Decision）                                            Warehouse Admin   Non-SAP                          

  011        Good transfer between Plant in MSL storage location (Movement Type: 301)   Warehouse Admin   MIGO                             Good transfer between Plant in MSL storage location (Movement Type: 301)

  012        Transport Stock from plant to plant                                        Warehouse Admin   Non-SAP                          Transport Stock from plant to plant
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements-3 .LS_Heading-3}

For Home Control, below business scenarios are considered in practices.

- Plant to plant ( For example, from Singapore to China)

- Storage location to Storage location

- Subcontracting stock to Home Control self-own

- Self-Own to subcontracting stock

- Transfer Material to material (Old material code to new material code)

## HC Delegation Of Authority {#hc-delegation-of-authority-3 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-3 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-3 .LS_Heading-3}

- Inventory adjustment for unrestricted-use, quality inspection and blocked stock will be supported.

- Inventory at Subcontractor (Stock at Vendor) locations with quantity tracking are managed in Inventory management at the plant level, Special Stock 'O'.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-3 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-3 .LS_Heading-3}

- N/A

# Authorization Roles {#authorization-roles .LS_Heading-1}

1.  

2.  

3.  

<!-- -->

1.  
2.  
3.  
4.  

<!-- -->

4.  
5.  
6.  

## Authorization Roles {#authorization-roles-1 .LS_Heading-3}

+-------------------+-----------------------------------------------------------+--------------------------------+----------------------------------------+
| **Business Role** | **Role Description**                                      | **Authorization Restrictions** | **Baseline ZRS Role(s)**               |
+===================+===========================================================+================================+========================================+
| Warehouse Admin   | Role includes the following tasks related to procurement: | Std Roles                      | Z_SAP_BR_WAREHOUSE_CLERK_Plant         |
|                   |                                                           |                                |                                        |
|                   | - Posting goods receipts, returns, transferring, issues   |                                |                                        |
|                   |                                                           |                                |                                        |
|                   | - Document reversal in case of mistakes                   |                                |                                        |
|                   |                                                           |                                |                                        |
|                   | - Initiate and process outbound deliveries                |                                |                                        |
|                   |                                                           |                                |                                        |
|                   | - PO search                                               |                                |                                        |
|                   |                                                           |                                |                                        |
|                   | - Inventory Display                                       |                                |                                        |
+-------------------+-----------------------------------------------------------+--------------------------------+----------------------------------------+
| Purchasing Admin  | - Physical inventory                                      | Std Roles Display access.      | - Z_SAP_BR_MASTER_DATA_VIEW_Plant      |
+-------------------+-----------------------------------------------------------+--------------------------------+----------------------------------------+
| Finance           | - Post physical inventory documents                       | Restricted by company code     | - Z\_ SAP_BR_AP_ACCOUNTANT_CompanyCode |
+-------------------+-----------------------------------------------------------+--------------------------------+----------------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

N/A

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

<!-- -->

6.  
7.  
8.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  ----------------------------------------------------------------------------
  **SAP App**                   **Description / Usage**
  ----------------------------- ----------------------------------------------
  Stock - Multiple Materials    A list of stock is displayed.

  Material Documents Overview   List of material documents

  Manage Manual Reservations    List of Manual Reservations

  Manage Reservation Items      List of Reservation Items
  ----------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                                                                |
+----------------------------------------+----------------------------------------+----------------+------------------+----------------+---------------------+
| **Report Name**                        | **Description**                        | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                                        |                                        |                |                  |                |                     |
|                                        |                                        |                | **SAP App/Rprt** |                |                     |
+:=======================================+:=======================================+:===============+:=================+:===============+:====================+
| Inventory Aging Report                 | Inventory Aging Report                 |                | /                | L3             | ZMM010D             |
+----------------------------------------+----------------------------------------+----------------+------------------+----------------+---------------------+
| Material Shelf-Life Review Report      | Material Shelf-Life Review Report      |                | /                | L3             | ZMM026              |
+----------------------------------------+----------------------------------------+----------------+------------------+----------------+---------------------+
| Material info record LT change history | Material info record LT change history |                | /                | L1             | ZMM030              |
+----------------------------------------+----------------------------------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+--------------------------------------------------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                                                             |
+---------------------------+---------------------------+------------------+------------------+----------------------------------------------+
| **Interface**             | **Description**           | **In Scope**     | **Complexity**   | **Comments**                                 |
+:==========================+:==========================+:=================+:=================+:=============================================+
| Material document -Create | Material document -Create |                  |                  | SAP standard API for posting goods receipts. |
+---------------------------+---------------------------+------------------+------------------+----------------------------------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

范围内需要切换的数据如下

+-------------------------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                                           |
+-----------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**                    | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|                             |                   |                           |                            | (# items)**   |                |
+:============================+:==================+:==========================+:===========================+===============+================+
| Physical Inventory count    | SAP ECC           |                           |                            |               |                |
+-----------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| Stock at Subcontract Vendor | SAP ECC           |                           |                            |               |                |
+-----------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified:

+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                                                                                                                 |
+---------------------------------+----------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| **Enhancement**                 | **Description**                                                                                    | **Complexity**    | **In Scope**      | **Comments**      |
+=================================+====================================================================================================+===================+===================+:==================+
| change Document date of 301&309 | Good Transfer 301&309 document date changing to goods receipt date in \"from plant\" by FIFO logic | L2                |                   |                   |
+---------------------------------+----------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+

## Forms {#forms .LS_Heading-3}

The following forms have been identified:

+---------------------------------------------------------------------------------------------------+
| **Forms**                                                                                         |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Form**          | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

## Programs {#programs .LS_Heading-3}

The following programs have been identified:

+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Programs**                                                                                                                                                                                         |
+-------------------+----------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| **Program**       | **Description**                                                                                                      | **Complexity**    | **In Scope**      | **Comments**      |
+===================+======================================================================================================================+===================+===================+===================+
| ZMM026A           | material Shelf-Life information maintains                                                                            | L1                |                   | ZMM026A           |
+-------------------+----------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| ZMM013            | Subcontracting Picklist Comparison：\                                                                                | L3                | Yes               | ZMM013            |
|                   | Automatic upload PO Item component List to S4HC;\                                                                    |                   |                   |                   |
|                   | Automatic BOM update in S4HC based on PO Item component List                                                         |                   |                   |                   |
+-------------------+----------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| ZMM300            | Automatic consumption of T-Items in S4HC\                                                                            | L3                | Yes               | ZMM300            |
|                   | Subcontracting turnkey item report                                                                                   |                   |                   |                   |
+-------------------+----------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| ZMM001/           | mass post goods movements of:\                                                                                       | L3                |                   | ZMM001/           |
|                   | 1. call \'BAPI_GOODSMVT_CREATE\' to post goods receipt of PO and goods transfer and Unplanned Goods Receipt & Issue\ |                   |                   |                   |
| ZMM017N/          | 2. Goods transfer in one step\                                                                                       |                   |                   | ZMM017N/          |
|                   | 3. Material Document Reversal                                                                                        |                   |                   |                   |
| ZMM029            |                                                                                                                      |                   |                   | ZMM029            |
+-------------------+----------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+

## Workflows {#workflows .LS_Heading-3}

The following workflows have been identified as in scope:

以下工作流被纳入范围：

+---------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                             |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**      | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image7.png){width="6.345306211723535in" height="2.3656714785651793in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
