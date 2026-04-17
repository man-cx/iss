**Return to Vendor**

**供应商退货**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_MM04_Return to Vendor**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Meos Xu                 MM Lead                08/06/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Jelly Ding              Purchasing          

     Yu Xiaodong              Purchasing          

      Cherry Qu               Purchasing          

     Xiaoqin Zhuo            Procurement          

      Lin Zhang              Procurement          

     Nancy Zhang                 SCM              

      Sally Jin           Finance - AP/cash       

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [4](#design-document-approval-options)](#design-document-approval-options)

[2. Return to Vendor [4](#return-to-vendor)](#return-to-vendor)

[2.1 Introduction [4](#introduction)](#introduction)

[2.2 Purpose [5](#purpose)](#purpose)

[2.3 Business Reason [5](#business-reason)](#business-reason)

[2.4 Business Benefits [5](#business-benefits)](#business-benefits)

[2.5 Business Process Flow [6](#business-process-flow)](#business-process-flow)

[Business Process Steps [7](#business-process-steps)](#business-process-steps)

[2.6 Home Control Business Requirements [7](#home-control-business-requirements)](#home-control-business-requirements)

[2.7 HC Delegation Of Authority [8](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[2.8 Standard Documents / Settings [8](#standard-documents-settings)](#standard-documents-settings)

[2.8.1 Purchase Orders [8](#purchase-orders)](#purchase-orders)

[2.9 Design Considerations / Key Assumptions [9](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[2.10 Support / Closing Considerations [9](#support-closing-considerations)](#support-closing-considerations)

[2.11 Integration Dependencies [9](#integration-dependencies)](#integration-dependencies)

[3. Authorization Roles [9](#authorization-roles)](#authorization-roles)

[3.1 Authorization Roles [9](#authorization-roles-1)](#authorization-roles-1)

[4. Document Types and Document Flow [10](#document-types-and-document-flow)](#document-types-and-document-flow)

[5. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [10](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[5.1 Reports [10](#reports)](#reports)

[5.1.1 Standard Reports [10](#standard-reports)](#standard-reports)

[5.1.2 HC Requested Reports [11](#hc-requested-reports)](#hc-requested-reports)

[5.2 Interfaces [11](#interfaces)](#interfaces)

[5.3 Conversions [11](#conversions)](#conversions)

[5.4 Programs [12](#programs)](#programs)

[5.5 Enhancements [12](#enhancements)](#enhancements)

[5.6 Forms [12](#forms)](#forms)

[5.7 Workflows [13](#workflows)](#workflows)

[6. Legend for Process Flow [13](#legend-for-process-flow)](#legend-for-process-flow)

> **\**

**Document Version History**

  ------------- ------------------------------------------------------------------------------------------------------ --------------------
   **Version**                                          **Summary of Change**                                           **Effective Date**

       1.0                                   Create the initial version of the document.                                    08/06/2025

       1.1       Add two PO types: return PO and replacement PO. Change process owner to quality and warehouse admin.       08/15/2025

                                                                                                                       
  ------------- ------------------------------------------------------------------------------------------------------ --------------------

> 

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

# Return to Vendor {#return-to-vendor .LS_Heading-1}

1.  

## Introduction {#introduction .LS_Heading-3}

The document focuses on a scenario return of procured materials back to vendor when there is an issue with quality or transit damage etc.

## Purpose {#purpose .LS_Heading-3}

> The return to vendor process begins with a requirement to return an item to a vendor. The Buyer will then create a Return PO in the system. The return PO is similar to a standard PO except for the return flag which sets up the return delivery to enable shipment of the item(s) back to the vendor.
>
> The Return PO confirmation goes to the Vendor and the Return Delivery is sent to the Shipping department where the item(s) are picked and shipped back along with a Delivery Note. When the Shipping department creates the delivery the item(s) are relieved from inventory. A credit memo is generated which relieves the liability to the vendor.

## Business Reason {#business-reason .LS_Heading-3}

> Returns to vendor and store returns (returns from plant to plant) can be necessary for the following reasons.
>
> • The vendor asks for the merchandise to be returned
>
> • Goods have to be returned/destroyed because they are spoiled, broken or of inferior quality
>
> • Returning discontinued articles to the vendor.
>
> • Incorrect parts were shipped.

## Business Benefits {#business-benefits .LS_Heading-3}

- Efficient and cost-effective streamlined return processes

- Ensure highly automated processes for the return of materials

- Reduce manual effort

- Real-time monitoring of the return progress

- Analytical list page: Monitor purchase order items

##  {#section .LS_Heading-3}

## Business Process Flow {#business-process-flow .LS_Heading-3}

![](media/media/image2.emf)

##  {#section-1 .LS_Heading-3}

## Business Process Steps  {#business-process-steps .LS_Heading-3}

+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| **Step** | **Step Name**                                      | **Role**               | **SAP App Name**             | **Expected Results**                                                                                                                     |
+==========+====================================================+========================+==============================+==========================================================================================================================================+
| 001      | Need for return goods                              | Quality                | Non-SAP                      | Need for return goods                                                                                                                    |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 002      | Return or replacement?                             | Quality                | /                            | Check if it is for return or replacement.                                                                                                |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 003      | Have post invoice?                                 | Warehouse Admin        | /                            | Check if AP admin has post invoice.                                                                                                      |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 004      | Create return PO                                   | Purchasing/Procurement | ME21N/Manage purchase orders | Create return PO by check the \"Return\" box of PO item.                                                                                 |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 005      | Examine material stock                             | Warehouse Admin        | Stock - Multiple Materials\  | Check the stock.                                                                                                                         |
|          |                                                    |                        | Stock - Single Material      |                                                                                                                                          |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 006      | material stock transfer(optional)                  | Warehouse Admin        | MIGO/Custom APP              | Transfer stock from block or other storage location to return storage location.                                                          |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 007      | post goods issue for return PO                     | Warehouse Admin        | MIGO/Custom APP              | Post goods issue for return.                                                                                                             |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 008      | Post credit memo                                   | AP admin               | MIRO/supplier invoice list   | Post credit memo                                                                                                                         |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 009      | material stock transfer(optional)                  | Warehouse Admin        | MIGO/Custom APP              | Transfer stock from block or other storage location to return storage location.                                                          |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 010      | post goods issue in original PO                    | Warehouse Admin        | MIGO/Custom APP              | Post goods issue for return.                                                                                                             |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 011      | post goods receipts for replacement in original PO | Warehouse Admin        | MIGO/Custom APP              | post goods receipts for replacement in original PO                                                                                       |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 012      | post supplier invoice                              | AP admin               | MIRO/supplier invoice list   | Post supplier invoice.                                                                                                                   |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 013      | Create PO with return and replacement item         | Purchasing/Procurement | ME21N/Manage purchase orders | Create PO with two items- return item by check the \"Return\" box and replacement item.                                                  |
|          |                                                    |                        |                              |                                                                                                                                          |
|          |                                                    |                        |                              | For this PO, check the "Final Invoice Indicator" box of "invoice" tab in PO items, thus AP admin do not need to post invoice for the PO. |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 014      | material stock transfer(optional)                  | Warehouse Admin        | MIGO/Custom APP              | Transfer stock from block or other storage location to return storage location.                                                          |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 015      | post goods issue for return item                   | Warehouse Admin        | MIGO/Custom APP              | Post goods issue for return.                                                                                                             |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
| 016      | post goods receipts for replacement item           | Warehouse Admin        | MIGO/Custom APP              | post goods receipts for replacement item                                                                                                 |
+----------+----------------------------------------------------+------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+

## Home Control Business Requirements {#home-control-business-requirements .LS_Heading-3}

- The buyer or SE will enter the item to be returned in SAP to initiate the return by entering a purchase order item with the "Returns Item" indicator selected.

- When the item(s) have been physically returned for a Stock Item and a Post Goods Issue/return is performed, the inventory will be relieved from inventory. For returns of expensed items, the consumption/expense will be reversed.

- If a credit is expected from a vendor, finance will enter a credit memo against the corresponding Purchase Order. (Ref: AP Payment Processing).

- If a credit is NOT expected, whether or not a replacement is expected, the buyer is required to mark the "final Invoice" indicator for the specified line item.

- Scenario A) -- Confirm return without replacement:

  - The purchasing department creates a return purchase order.

  - The warehouse returns the goods.

  - The supplier provides a credit note for the finance department to post.

- Scenario B) -- When replacing goods and the finance department has not yet performed invoice verification:

  - The warehouse returns the goods based on the original purchase order (PO).

  - The undelivered quantity of the PO is released.

  - The supplier delivers the goods again.

  - The warehouse receives the goods again.

  - The finance department performs invoice verification.

- Scenario C) -- When replacing goods and the finance department has already performed invoice verification:

  - The purchasing department creates a new purchase order containing both a return line and a replacement receipt line; on the \"Invoice\" tab of these two-line items in the PO, check the \"Final Invoice Indicator\" -- this ensures the finance department will not perform invoice verification for this return-and-replacement PO.

  - The warehouse returns the goods.

  - The warehouse receives the replacement goods.

- The ability to specify or change the stock type and storage location of the material to be returned on PO Entry.

- Forms for Change PO's -- Standard PO forms will be used

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Purchase Orders {#purchase-orders .LS_Heading-3}

  -----------------------------------------------------------------------------------------------------
  **Document Type**   **Description**                          **Comments**
  ------------------- ---------------------------------------- ----------------------------------------
  ZN1                 Repeating Procurement for CN8F           For replacement of original PO

  ZN2                 Repeating Procurement for CN7F           For replacement of original PO

  ZN3                 Repeating Procurement for SG28           For replacement of original PO

  ZN4                 Repeating Procurement for CN8C           For replacement of original PO

  ZN5                 Repeating Procurement for CN8B           For replacement of original PO

  ZN6                 Repeating Procurement for CN8E           For replacement of original PO

  ZN7                 Repeating Procurement for CN7B           For replacement of original PO

  ZN8                 Repeating Procurement for US10           For replacement of original PO

  ZN9                 Repeating Procurement for BE10           For replacement of original PO

  ZN10                Repeating Procurement for IN10           For replacement of original PO

  ZN11                Repeating Procurement for CN8A           For replacement of original PO

  ZN12                Repeating Procurement for CN7A           For replacement of original PO

  ZN13                Repeating Procurement for CN7C           For replacement of original PO

  ZRT                 Return w/o replacement Purchase Order    Return w/o replacement Purchase Order

  ZRP                 Return with replacement Purchase Order   Return with replacement Purchase Order
  -----------------------------------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

## Integration Dependencies {#integration-dependencies .LS_Heading-3}

- Postings can only be made in accounting periods open for posting.

- Postings in materials management can only be made in current and previous period. These must be in synch with open accounting periods.

- All purchased material masters must have a return storage location created to exclude returned material from MRP.

# Authorization Roles {#authorization-roles .LS_Heading-1}

2.  

## Authorization Roles {#authorization-roles-1 .LS_Heading-3}

+-----------------------------+-----------------------------------------------------------------------------+--------------------------------+----------------------------------------+
| **Business Role**           | **Role Description**                                                        | **Authorization Restrictions** | **Baseline ZRS Role(s)**               |
+=============================+=============================================================================+================================+========================================+
| Purchasing                  | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                      | - Z\_ SAP_BR_PURCHASER_Plant           |
|                             |                                                                             |                                |                                        |
|                             | - Monitor PO status                                                         |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - Process PO output on demand                                               |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - Display purchasing master data -- purchasing info records and source list |                                |                                        |
+-----------------------------+-----------------------------------------------------------------------------+--------------------------------+----------------------------------------+
| Procurement                 | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                      | - Z\_ SAP_BR_PROCUREMENT_Plant         |
|                             |                                                                             |                                |                                        |
|                             | - Monitor PO status                                                         |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - Process PO output on demand                                               |                                |                                        |
+-----------------------------+-----------------------------------------------------------------------------+--------------------------------+----------------------------------------+
| Warehouse Admin             | Role includes the following tasks related to procurement:                   | Std Roles                      | Z_SAP_BR_WAREHOUSE_CLERK_Plant         |
|                             |                                                                             |                                |                                        |
|                             | - Posting goods receipts, returns                                           |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - Document reversal in case of mistakes                                     |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - Initiate and process outbound deliveries in case of vendor returns        |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - PO search                                                                 |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - Inventory Display                                                         |                                |                                        |
+-----------------------------+-----------------------------------------------------------------------------+--------------------------------+----------------------------------------+
| Purchasing Reporting        | - Purchasing analytics                                                      | Std Roles Display access.      | - Z_SAP_BR_MASTER_DATA_VIEW_Plant      |
|                             |                                                                             |                                |                                        |
|                             | - All purchasing reports and list displays w/o create/update access         |                                |                                        |
+-----------------------------+-----------------------------------------------------------------------------+--------------------------------+----------------------------------------+
| Accounts Payable Accountant | - Enter vendor invoices, credit memos                                       | Restricted by company code     | - Z\_ SAP_BR_AP_ACCOUNTANT_CompanyCode |
|                             |                                                                             |                                |                                        |
|                             | - Process blocked invoices                                                  |                                |                                        |
|                             |                                                                             |                                |                                        |
|                             | - Process vendor payments                                                   |                                |                                        |
+-----------------------------+-----------------------------------------------------------------------------+--------------------------------+----------------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------
  ZN1                     Repeating Procurement for CN8F

  ZN2                     Repeating Procurement for CN7F

  ZN3                     Repeating Procurement for SG28

  ZN4                     Repeating Procurement for CN8C

  ZN5                     Repeating Procurement for CN8B

  ZN6                     Repeating Procurement for CN8E

  ZN7                     Repeating Procurement for CN7B

  ZN8                     Repeating Procurement for US10

  ZN9                     Repeating Procurement for BE10

  ZN10                    Repeating Procurement for IN10

  ZN11                    Repeating Procurement for CN8A

  ZN12                    Repeating Procurement for CN7A

  ZN13                    Repeating Procurement for CN7C

  ZRT                     Return w/o replacement Purchase Order

  ZRP                     Return with replacement Purchase Order
  -----------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

3.  

4.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

+-------------------------------+-------------------------------------------------------------------------------------------------+
| **SAP App**                   | **Description / Usage**                                                                         |
+===============================+=================================================================================================+
| Procurement Overview          | KPI monitor and launchpad for crucial procurement task such as monitoring POs, PRs, spend, etc. |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| My Purchasing Documents Items | Monitor and manage all documents related to purchasing -- PRs, POs, goods receipts, invoices    |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Manage Purchase Orders        | List and manage POs                                                                             |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Manage Purchase Requisitions  | List and manage PRs                                                                             |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Manage Scheduling Agreements  | List and manage scheduling agreements                                                           |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Monitor purchase order items  | List and monitor status of open POs                                                             |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Procurement Analytics         | A collection of live expandable tiles with pre-configured KPI, including:                       |
|                               |                                                                                                 |
|                               | - Overdue POs                                                                                   |
|                               |                                                                                                 |
|                               | - Purchasing spend analysis                                                                     |
|                               |                                                                                                 |
|                               | - Supplier evaluations (by time)                                                                |
|                               |                                                                                                 |
|                               | - Purchasing group (buyer) activity                                                             |
|                               |                                                                                                 |
|                               | - Average PO delivery time                                                                      |
|                               |                                                                                                 |
|                               | - PR approval time                                                                              |
|                               |                                                                                                 |
|                               | PR to PO cycle time                                                                             |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Stock - Multiple Materials    | List the stock of materials.                                                                    |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| supplier invoice list         | supplier invoice list                                                                           |
+-------------------------------+-------------------------------------------------------------------------------------------------+

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+--------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                  |
+-----------------+-----------------+----------------+------------------+----------------+---------------------+
| **Report Name** | **Description** | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                 |                 |                |                  |                |                     |
|                 |                 |                | **SAP App/Rprt** |                |                     |
+:================+:================+:===============+:=================+:===============+:====================+
| N/A             |                 |                |                  |                |                     |
+-----------------+-----------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+----------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                     |
+-------------------+-------------------+-------------------+-------------------+--------------------+
| **Interface**     | **Description**   | **In Scope**      | **Complexity**    | **Comments**       |
+:==================+:==================+:==================+:==================+:===================+
| N/A               |                   |                   |                   |                    |
+-------------------+-------------------+-------------------+-------------------+--------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

+-------------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                               |
+----------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| **Data**       | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\      | **Complexity** |
|                |                   |                           |                            | (# items)**    |                |
+================+===================+===========================+============================+================+================+
| N/A            |                   |                           |                            |                |                |
+----------------+-------------------+---------------------------+----------------------------+----------------+----------------+

## Programs {#programs .LS_Heading-3}

The following solution programs have been identified as in scope:

+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Programs**                                                                                                                                                                                                |
+---------------------------+---------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| **Program**               | **Description**                                                                                                     | **Complexity**    | **In Scope**      | **Comments**      |
+===========================+=====================================================================================================================+===================+===================+:==================+
| Mass post goods movements | mass post goods movements of :\                                                                                     | L3                | No                |                   |
|                           | 1.call \'BAPI_GOODSMVT_CREATE\' to post goods receipt of PO and goods transfer and Unplanned Goods Receipt & Issue\ |                   |                   |                   |
|                           | 2. Goods transfer in one step\                                                                                      |                   |                   |                   |
|                           | 3. Material Document Reversal                                                                                       |                   |                   |                   |
+---------------------------+---------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+---------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                                                                        |
+--------------------------------------------+--------------------------------------------+------------------+------------------+-------------------------+
| **Enhancement**                            | **Description**                            | **Complexity**   | **In Scope**     | **Comments**            |
+============================================+============================================+==================+==================+:========================+
| custom logic - send email to PO creator    | custom logic - send email to PO creator    | L1               | No               |                         |
+--------------------------------------------+--------------------------------------------+------------------+------------------+-------------------------+
| custom logic of cannot change BOM PO price | custom logic of cannot change BOM PO price | L1               | No               | For direct procurement  |
+--------------------------------------------+--------------------------------------------+------------------+------------------+-------------------------+

## Forms {#forms .LS_Heading-3}

The following forms have been identified as in scope:

+------------------------------------------------------------------------------------------------------------------------+
| **Forms**                                                                                                              |
+-------------------+-----------------------+-------------------+-------------------+------------------------------------+
| **Form**          | **Description**       | **Complexity**    | **In Scope**      | **Comments**                       |
+===================+=======================+===================+===================+====================================+
| Purchase Order    | Custom PO output form | Small             | Yes               | New Form need to be created for ZH |
+-------------------+-----------------------+-------------------+-------------------+------------------------------------+
| Purchase Order    | Custom PO output form | Small             | Yes               | New Form need to be created for EN |
+-------------------+-----------------------+-------------------+-------------------+------------------------------------+

## Workflows {#workflows .LS_Heading-3}

The following workflows have been identified as in scope:

+---------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                             |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**      | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image3.png){width="6.345306211723535in" height="2.3656714785651793in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems
