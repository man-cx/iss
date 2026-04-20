**External Subcontracting**

**委外采购**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_MM03_External Subcontracting**

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

[2. Subcontracting [4](#subcontracting)](#subcontracting)

[2.1 Purpose [4](#purpose)](#purpose)

[2.2 Business Reason [5](#business-reason)](#business-reason)

[2.3 Business Benefits [5](#business-benefits)](#business-benefits)

[2.4 Business Process Flow [6](#business-process-flow)](#business-process-flow)

[Business Process Steps [7](#business-process-steps)](#business-process-steps)

[2.5 Home Control Business Requirements [8](#home-control-business-requirements)](#home-control-business-requirements)

[2.6 HC Delegation Of Authority [8](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[2.7 Standard Documents / Settings [8](#standard-documents-settings)](#standard-documents-settings)

[2.7.1 Purchase Orders [8](#purchase-orders)](#purchase-orders)

[2.8 Design Considerations / Key Assumptions [9](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[2.9 Support / Closing Considerations [9](#support-closing-considerations)](#support-closing-considerations)

[2.10 Integration Dependencies [9](#integration-dependencies)](#integration-dependencies)

[3. Authorization Roles [9](#authorization-roles)](#authorization-roles)

[3.1 Authorization Roles [9](#authorization-roles-1)](#authorization-roles-1)

[4. Document Types and Document Flow [10](#document-types-and-document-flow)](#document-types-and-document-flow)

[5. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [11](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[5.1 Reports [11](#reports)](#reports)

[5.1.1 Standard Reports [11](#standard-reports)](#standard-reports)

[5.1.2 HC Requested Reports [11](#hc-requested-reports)](#hc-requested-reports)

[5.2 Interfaces [12](#interfaces)](#interfaces)

[5.3 Conversions [12](#conversions)](#conversions)

[5.4 Programs [12](#programs)](#programs)

[5.5 Enhancements [13](#enhancements)](#enhancements)

[5.6 Forms [13](#forms)](#forms)

[5.7 Workflows [13](#workflows)](#workflows)

[6. Legend for Process Flow [14](#legend-for-process-flow)](#legend-for-process-flow)

> **\**

**Document Version History**

  ------------- ------------------------------------------------------- --------------------
   **Version**                   **Summary of Change**                   **Effective Date**

       1.0            Create the initial version of the document.            08/06/2025

       1.1       Change the process of T-items as meeting and comments       08/13/2025

       1.2                           Add PO types                            08/15/2025
  ------------- ------------------------------------------------------- --------------------

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

# Subcontracting {#subcontracting .LS_Heading-1}

1.  

## Purpose {#purpose .LS_Heading-3}

> Purposed of this scenario is to address the procurement of materials on subcontracting basis.
>
> A Subcontract Purchase Requisition is either generated via the Material Requirements Planning process or manually by a planner. A Buyer will validate the accuracy of the Purchase Requisition and convert it into a Purchase Order. The purchase order is subject to approval based on predefined parameters prior to being issued to a vendor (non MRP).
>
> Components of the finished material are provided to vendor and monitored.
>
> The consumption of sent materials is recorded upon receipt of the value-added completed material. The vendor sends the invoice for the services provided which is paid during the normal payment cycle.

## Business Reason {#business-reason .LS_Heading-3}

> The material to be produced by the vendor can be ordered as a subcontract item in a purchase requisition, purchase order. Each subcontract item has one or more sub-items that contain the individual components the vendor needs to perform the subcontract work or value-added service.

## Business Benefits {#business-benefits .LS_Heading-3}

- Streamline subcontracting processes efficiently and cost-effectively

- Ensure highly automated processes

- Reduce manual effort greatly

- Monitor the process progress in real-time

## Business Process Flow {#business-process-flow .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps  {#business-process-steps .LS_Heading-3}

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Step**   **Step Name**                                                **Role**                            **SAP App Name**                     **Expected Results**
  ---------- ------------------------------------------------------------ ----------------------------------- ------------------------------------ -------------------------------------------------------------------------------------------------
  001        HC_SAP_DD_PP02_02_MRP Run                                    Planner                             /                                    MRP run

  002        Process subcontracting PR to PO                              Purchasing/PR (procurement agent)   Process Purchase Requisitions(V2)    Process PR to subcontracting PO

  003        HC_SAP_DD_MM07_01_Post Goods Receipts for RM                 Warehouse admin                     /                                    Post goods receipts for RM

  004        Display and export BOM to subcontractor                      Purchasing/PR (procurement agent)   Manage Multilevel Bill of Material   Export BOM to subcontractor

  005        If 2nd Tier subcontractor?                                   Purchasing/PR (procurement agent)   /                                    

  006        Sub-contractor prepares RM (including T-items) for staging   1st Tier subcontractor              Non-SAP                              Sub-contractor prepares RM (including T-items) for staging

  007        Production of FG is completed                                1st Tier subcontractor              Non-SAP                              Production of FG is completed

  008        Sub-contractor prepares RM (including T-items) for staging   2nd Tier subcontractor              Non-SAP                              Sub-contractor prepares RM (including T-items) for staging

  009        Manufacture the sub-assemblies                               2nd Tier subcontractor              Non-SAP                              Manufacture the sub-assemblies

  010        Receive sub-assemblies from 2nd tier sub-contractor          1st Tier subcontractor              Non-SAP                              Receive sub-assemblies from 2nd tier sub-contractor

  011        GR for sub-assemblies & Backflush                            Warehouse admin                     MIGO                                 GR for sub-assemblies & Backflush

  012        sub-contractor picks list consumption adjustment             Warehouse admin                     Custom APP in SAP BTP                Comparation of pick list and consumption and adjust components in PO items.

  013        GR for T-items                                               Warehouse admin                     Custom APP in SAP BTP                Post goods receipts for T-items by T-items POs, which are created in the Custom APP in SAP BTP.

  014        GR for FG & Backflush                                        Warehouse admin                     MIGO                                 Post FG goods receipts.
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Home Control Business Requirements {#home-control-business-requirements .LS_Heading-3}

- Production at the sub-contractor site is based on a Weekly Production Schedule generated and sent by Home Control. All input materials required for production are provided by Home Control except turnkey items, which are procured by the sub-contractor and sold to Home Control. In cases of sub-assemblies which are processed by 2nd tier sub-contractors, Home Control generates the quantities of component materials to be issued from the 1st tier sub-contractor; the 1st tier sub-contractor then packs and ships the required materials.

- All sub-contractor purchasing transactions will be executed within SAP, and the Procurement department will be the key owner of the sub-contracting process.

- Home Control currently purchases a number of component materials from its Sub-contractors; these are labelled turnkey items (T-items). There is a Z-report (ZMM300) currently in use within the SAP ECC system which automatically does goods receipt for these T-items, which should be also made available in the new SAP system. These T-items will be posted goods receipts in the Z\*program (was called ZMM300) by Pos, which are created in the Z\*programs (was called ZMM300) before posting.

- For all T-items, purchasing and procurements do not need to create PO.

- There is a Z-report (ZMM013) currently in use within the SAP ECC system which displays the pick list adjustments made at the Sub-contractor site; this enables Home Control to make corresponding adjustments for any part replacements and/or quantity changes, and should be made available in the new SAP system.

- Requisitions created by MRP, including subcontracting requisitions, will not require approval.

- Subcontracting POs against requisitions will not require any additional approvals.

- All subcontracting purchases shall require a 3-way match.

- Purchasing shall be able maintain vendor subcontracting (service) pricing information and approved vendor lists (source lists).

- PO output shall be available to buyers as PDF documents, who will process the output as needed (either call vendor or forward the email). No additional outputs (EDI, XML, fax, etc.) shall be required.

- Buyers will monitor the necessary inventory movements to reflect work-in-process at these value-added vendors (ME2O) Display Subcontracting Stocks by supplier and the Subcontracting Cockpit FIORI Apps.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Purchase Orders {#purchase-orders .LS_Heading-3}

  -------------------------------------------------------------------------------------
  **Document Type**   **Description**                  **Comments**
  ------------------- -------------------------------- --------------------------------
  ZN1                 Repeating Procurement for CN8F   Repeating Procurement for CN8F

  ZN2                 Repeating Procurement for CN7F   Repeating Procurement for CN7F

  ZN3                 Repeating Procurement for SG28   Repeating Procurement for SG28

  ZN4                 Repeating Procurement for CN8C   Repeating Procurement for CN8C

  ZN5                 Repeating Procurement for CN8B   Repeating Procurement for CN8B

  ZN6                 Repeating Procurement for CN8E   Repeating Procurement for CN8E

  ZN7                 Repeating Procurement for CN7B   Repeating Procurement for CN7B

  ZN8                 Repeating Procurement for US10   Repeating Procurement for US10

  ZN9                 Repeating Procurement for BE10   Repeating Procurement for BE10

  ZN10                Repeating Procurement for IN10   Repeating Procurement for IN10

  ZN11                Repeating Procurement for CN8A   Repeating Procurement for CN8A

  ZN12                Repeating Procurement for CN7A   Repeating Procurement for CN7A

  ZN13                Repeating Procurement for CN7C   Repeating Procurement for CN7C
  -------------------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

## Integration Dependencies {#integration-dependencies .LS_Heading-3}

- Procurement of subcontracting is tightly integrated with other business processes, such as:

  - Materials forecasting and planning

  - Inventory and warehouse management

  - Quality management

  - Accounting

- General ledger postings resulting from goods receipts, consumption of components, and invoice postings will be configured in financial accounting.

# Authorization Roles {#authorization-roles .LS_Heading-1}

2.  

## Authorization Roles {#authorization-roles-1 .LS_Heading-3}

+----------------------+-----------------------------------------------------------------------------+--------------------------------+--------------------------------------+
| **Business Role**    | **Role Description**                                                        | **Authorization Restrictions** | **Baseline ZRS Role(s)**             |
+======================+=============================================================================+================================+======================================+
| Planner              | Role includes the following key [system]{.underline} tasks:                 | Std Roles                      | - Z_SAP_BR_MATL_PLNR_EXT_PROC\_Plant |
|                      |                                                                             |                                |                                      |
|                      | - Execute MRP and monitor results                                           |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Manage MRP data in material master                                        |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Manage planned independent requirements                                   |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Execute material forecast                                                 |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Monitor inventory                                                         |                                |                                      |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+--------------------------------------+
| Purchasing           | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                      | - Z\_ SAP_BR_PURCHASER_Plant         |
|                      |                                                                             |                                |                                      |
|                      | - Monitor PO status                                                         |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Process PO output on demand                                               |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Manage open PRs                                                           |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Display purchasing master data -- purchasing info records and source list |                                |                                      |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+--------------------------------------+
| Procurement          | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                      | - Z\_ SAP_BR_PROCUREMENT_Plant       |
|                      |                                                                             |                                |                                      |
|                      | - Monitor PO status                                                         |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Process PO output on demand                                               |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Manage open PRs                                                           |                                |                                      |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+--------------------------------------+
| Warehouse Admin      | Role includes the following tasks related to procurement:                   | Std Roles                      | Z_SAP_BR_WAREHOUSE_CLERK_Plant       |
|                      |                                                                             |                                |                                      |
|                      | - Posting goods receipts, returns                                           |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Document reversal in case of mistakes                                     |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Initiate and process outbound deliveries in case of vendor returns        |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - PO search                                                                 |                                |                                      |
|                      |                                                                             |                                |                                      |
|                      | - Inventory Display                                                         |                                |                                      |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+--------------------------------------+
| Purchasing Reporting | - Purchasing analytics                                                      | Std Roles Display access.      | - Z_SAP_BR_MASTER_DATA_VIEW_Plant    |
|                      |                                                                             |                                |                                      |
|                      | - All purchasing reports and list displays w/o create/update access         |                                |                                      |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+--------------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------
  ZN1                     Repeating Procurement for CN8F

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
  -----------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

3.  

4.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  -----------------------------------------------------------------------------------------------------------------------------------
  **SAP App**                          **Description / Usage**
  ------------------------------------ ----------------------------------------------------------------------------------------------
  Procurement Overview                 KPI monitor and launchpad for crucial procurement task such as monitoring POs, PRs, etc.

  My Purchasing Documents Items        Monitor and manage all documents related to purchasing -- PRs, POs, goods receipts, invoices

  Manage Purchase Orders               List and manage POs

  Manage Purchase Requisitions         List and manage PRs

  Manage Scheduling Agreements         List and manage scheduling agreements

  Monitor purchase order items         List and monitor status of open POs

  Material Documents Overview          Display Material Documents

  Manage Multilevel Bill of Material   Display Multilevel Bill of Material
  -----------------------------------------------------------------------------------------------------------------------------------

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

+----------------------------------------------------------------------------------------------------------------------------------------------+
| **Programs**                                                                                                                                 |
+-------------------+--------------------------------------------------------------+-------------------+-------------------+-------------------+
| **Program**       | **Description**                                              | **Complexity**    | **In Scope**      | **Comments**      |
+===================+==============================================================+===================+===================+:==================+
| ZMM013            | Subcontracting Picklist Comparison：\                        | L3                | Yes               |                   |
|                   | Automatic upload PO Item component List to S4HC;\            |                   |                   |                   |
|                   | Automatic BOM update in S4HC based on PO Item component List |                   |                   |                   |
+-------------------+--------------------------------------------------------------+-------------------+-------------------+-------------------+
| ZMM300            | Automatic consumption of T-Items in S4HC                     | L3                | Yes               |                   |
|                   |                                                              |                   |                   |                   |
|                   | Create PO for T-items\                                       |                   |                   |                   |
|                   | Subcontracting turnkey item report                           |                   |                   |                   |
+-------------------+--------------------------------------------------------------+-------------------+-------------------+-------------------+

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
