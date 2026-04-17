**Stock Transfer Order**

**库存转储订单**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_MM05_Stock Transfer Order**

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

[2. KIT Stock Transfer [6](#kit-stock-transfer)](#kit-stock-transfer)

[2.1 Purpose [6](#purpose)](#purpose)

[2.2 Business Reason [7](#business-reason)](#business-reason)

[2.3 Business Benefits [7](#business-benefits)](#business-benefits)

[2.4 Business Process for KIT Stock Transfer [7](#business-process-for-kit-stock-transfer)](#business-process-for-kit-stock-transfer)

[▪ Business Process Steps [7](#business-process-steps)](#business-process-steps)

[2.5 HC Functional Requirements [8](#hc-functional-requirements)](#hc-functional-requirements)

[2.6 HC Delegation Of Authority [8](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[2.7 Standard Documents / Settings [9](#standard-documents-settings)](#standard-documents-settings)

[2.7.1 Movement Type [9](#movement-type)](#movement-type)

[2.8 Design Considerations / Key Assumptions [9](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[2.9 Cross Functional Integration Dependencies [9](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[2.10 Support / Closing Considerations [9](#support-closing-considerations)](#support-closing-considerations)

[3. B&S Stock Transfer Order [9](#bs-stock-transfer-order)](#bs-stock-transfer-order)

[3.1 Purpose [9](#purpose-1)](#purpose-1)

[3.2 Business Reason [9](#business-reason-1)](#business-reason-1)

[3.3 Business Benefits [10](#business-benefits-1)](#business-benefits-1)

[3.4 Planned Independent Requirements and MRP [10](#planned-independent-requirements-and-mrp)](#planned-independent-requirements-and-mrp)

[3.5 Purchase Requisition [10](#purchase-requisition)](#purchase-requisition)

[3.6 Purchase Order [10](#purchase-order)](#purchase-order)

[3.7 Business Process for B&S Stock Transfer Order [12](#business-process-for-bs-stock-transfer-order)](#business-process-for-bs-stock-transfer-order)

[▪ Business Process Steps [13](#business-process-steps-1)](#business-process-steps-1)

[3.8 HC Functional Requirements [14](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[3.9 HC Delegation Of Authority [15](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[3.10 Standard Documents / Settings [15](#standard-documents-settings-1)](#standard-documents-settings-1)

[3.10.1 Purchase Requisitions [15](#purchase-requisitions)](#purchase-requisitions)

[3.10.2 Purchase Orders [15](#purchase-orders)](#purchase-orders)

[3.11 Design Considerations / Key Assumptions [15](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[3.12 Cross Functional Integration Dependencies [15](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[3.13 Support / Closing Considerations [15](#support-closing-considerations-1)](#support-closing-considerations-1)

[4. Authorization Roles [16](#authorization-roles)](#authorization-roles)

[6.2 Authorization Roles [16](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [17](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [17](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[8.1 Reports [17](#reports)](#reports)

[8.1.1 Standard Reports [17](#standard-reports)](#standard-reports)

[8.1.2 HC Requested Reports [18](#hc-requested-reports)](#hc-requested-reports)

[8.2 Interfaces [18](#interfaces)](#interfaces)

[8.3 Conversions [18](#conversions)](#conversions)

[8.4 Enhancements [19](#enhancements)](#enhancements)

[8.5 Forms [19](#forms)](#forms)

[8.6 Workflows [19](#workflows)](#workflows)

[7. Legend for Process Flow [20](#legend-for-process-flow)](#legend-for-process-flow)

> **\**

**Document Version History**

+:-----------:+:-------------------------------------------:+:------------------:+
| **Version** | **Summary of Change**                       | **Effective Date** |
+-------------+---------------------------------------------+--------------------+
| 1.0         | Create the initial version of the document. | 08/06/2025         |
+-------------+---------------------------------------------+--------------------+
| 1.1         | Change the B&S STO owner and definition.    | 08/15/2025         |
|             |                                             |                    |
|             | Add requirements as comments                |                    |
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

# KIT Stock Transfer {#kit-stock-transfer .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

The stock transfer process begins with a requirement to transfer material from one company or plant to another company or plant within the same country.

For Home Control, demands of KIT materials are transfer from CN8E to CN8C, and the purchase requisitions with item category=U are generated when MRP running. Then Purchasing and procurement will not process the PR. After receiving the KIT in CN8C, warehouse admin directly posts goods transfer with movement type=301 from CN8C to CN8E.

## Business Reason {#business-reason .LS_Heading-3}

Material is transferring stock from a plant to another plant. For HC, it's from CN8C to CN8E.

## Business Benefits {#business-benefits .LS_Heading-3}

- Fulfill the requirement for intercompany stock transfer process between two companies.

- Leverage the stock balance between companies and reduce storage value.

## Business Process for KIT Stock Transfer {#business-process-for-kit-stock-transfer .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| **Step** | **Step Name**                                                                  | **Role**        | **SAP App Name**                 | **Expected Results**                                                                                          |
+==========+================================================================================+=================+==================================+===============================================================================================================+
| 001      | Need for Kitting                                                               | Sales           | Non-SAP                          | Need for FG                                                                                                   |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 002      | Examine Purchasing Info Record and source list of components                   | Purchasing      | Manage purchasing info record    | Examine Purchasing Info Record and source list of components                                                  |
|          |                                                                                |                 |                                  |                                                                                                               |
|          |                                                                                |                 | Manage source list               |                                                                                                               |
|          |                                                                                |                 |                                  |                                                                                                               |
|          |                                                                                |                 | Manage quota arrangement         |                                                                                                               |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 003      | HC_SAP_DD_MM01_03_Purchasing Info Record and Source List and Quota Arrangement | Purchasing      | /                                | Create or Change Purchasing Info Record and source list of components                                         |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 004      | Check MRP views of Material Master Data                                        | Purchasing      | MM02/Manage material master data | Check the MRP views of materials master data. Especially Special procurement type in MRP views and MRP areas. |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 005      | HC_SAP_DD_PP02_02_MRP Run                                                      | Planner         | /                                | Run MRP to generate PR.                                                                                       |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 006      | If electronic materials? (Decision)                                            | Planner         | /                                |                                                                                                               |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 007      | HC_SAP_DD_MM02_Procurement of Direct Materials in CN8E                         | Procurement     | /                                | Procurement for non- electronic materials in CN8E                                                             |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 008      | Demands transfer to CN8C                                                       | Procurement     |                                  |                                                                                                               |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 009      | HC_SAP_DD_MM03_External Subcontracting in CN8C                                 | Procurement     | /                                | Procurement for electronic materials in CN8C                                                                  |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 010      | Post goods receipts in CN8C                                                    | Warehouse Admin | MIGO                             | Post goods receipts for electronic materials in CN8C                                                          |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+
| 011      | Post goods transfer from CN8C to CN8E                                          | Warehouse Admin | MIGO                             | Post goods transfer from CN8C to CN8E                                                                         |
+----------+--------------------------------------------------------------------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- For Home Control, demands of KIT materials are transfer from CN8E to CN8C, and the purchase requisitions with item category=U are generated when MRP running. Then Purchasing and procurement will not process the PR. After receiving the KIT in CN8C, warehouse admin directly posts goods transfer with movement type=301 from CN8C to CN8E.

- For KIT stock transfer, the electronic materials master data in CN8E should be maintained by Special procurement Type = 40,and do not need to maintain info record in CN8E.

- The electronic materials should be maintained info record, and the price should be the same as CN8C's.

- The Kitting BOM should be created in CN8E.

- In CN8E, it is necessary to create sales views for all kitting material master data.

- In CN8C, it is necessary to create sales views for the master data of kitting electronic materials.

- In CN8C, it is necessary for IC programming materials(with package) to maintain BOM.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Movement Type {#movement-type .LS_Heading-3}

  ----------------------------------------------------------------------------------
  **Movement Type**   **Description**                **Comments**
  ------------------- ------------------------------ -------------------------------
  301                 Transfer from plant to plant   Transfer from plant to plant

  ----------------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- All inventory materials will have both purchasing and MRP views.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Procurement of direct materials is tightly integrated with other business processes, such as:

  - Materials forecasting and planning.

  - Inventory and warehouse management.

  - Accounting​**​**

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# B&S Stock Transfer Order {#bs-stock-transfer-order .LS_Heading-1}

3.  

<!-- -->

2.  

## Purpose {#purpose-1 .LS_Heading-3}

The stock transfer process begins with a requirement to transfer material from one company or plant to another company or plant within the same country. The Purchaser creates purchase orders under the receiving plant.

A warehouse clerk at the issuing plant monitors the materials due to be shipped and creates deliveries as required. Once the delivery is complete, the delivery quantities are issued, appropriate documentation is generated, and the goods are shipped, ending the process for the issuing plant.

Goods are received at the receiving plant referencing the purchase documents. Inventory is received into a storage location based on fixed parameters proposed from the material master, which can be changed at the time of transactional data capture (purchase order creation or goods receipt).

## Business Reason {#business-reason-1 .LS_Heading-3}

Material is transferring stock from a plant to another plant indifferent company code. For HC, it's in different company code.

In some cases, the STO between CN7F and CN8F is generated through MRP runs; in some cases, the STO is created manually.

Buy-Sell solution is proposed to Omni users when suppliers are not willing to do business with like plant CN7F (company =CN17, i.e. in RMB), and PR&PO has to be placed via inter-company plant CN8F (company= SG21, i.e. in USD) after CN8F purchased from suppliers.

This solution directly cascades demands loaded under 460145CN7F and 263156CN8F to plant CN8F, pushes inventory from CN8F to CN7F upon Post Goods Issue (PGI) at CN8F to minimize additional steps to create Stock Transfer Order (STO) in CN8F for CN7F demands, and inventory transfer from CN8F to CN7F.

## Business Benefits {#business-benefits-1 .LS_Heading-3}

- Fulfill the requirement for intercompany stock transfer process between two companies.

- Leverage the stock balance between companies and reduce storage value.

## Planned Independent Requirements and MRP {#planned-independent-requirements-and-mrp .LS_Heading-3}

A Planned Independent Requirement is a planned requirement for a material and a supply planning area without reference to a sales order. It contains a time series with the planned material requirements (Planned Independent Requirement items) and identifying and administrative information.

The requirement/demand for the product (finished) is generated either through Planned Independent Requirement or through Sales Order and dependent requirement is generated by the system once the MRP run is taken place based on their stocks availability during the Material Requirement Planning (MRP) run.

Material requirements planning will run periodically as scheduled to create supply elements for all existing demands. MRP creates a supply element if the expected supply is less than the expected demand on a certain date.

Material requirements planning will run periodically as scheduled to create supply elements for all.

## Purchase Requisition  {#purchase-requisition .LS_Heading-3}

Purchase Requisition is an internal Document instructing the purchasing department to request a specific good or service for a specified time.

In this scope, Purchase Requisitions can be created by MRP run.

## Purchase Order {#purchase-order .LS_Heading-3}

Purchase order is a legal document to request a vendor for a specific material or service under the stated conditions.

In this scope, the purchase orders can be processed from purchase requisitions and created without PR reference.

- **Purchase Order Output**

<!-- -->

- Once Purchase order is approved, the PO details can be communicated to the PO creator.

- Manually download a PDF copy of the purchase order and send it to the supplier.

- Send the PDF copy of purchase order via email manually via add a new output in PO, provided the email-id is assigned to the supplier master (BP).

## Business Process for B&S Stock Transfer Order {#business-process-for-bs-stock-transfer-order .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| **Step** | **Step Name**                                                                                 | **Role**            | **SAP App Name**                        | **Expected Results**                                                                                           |
+==========+===============================================================================================+=====================+=========================================+================================================================================================================+
| 001      | Need for FG                                                                                   | Sales               | Non-SAP                                 | Need for FG                                                                                                    |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 002      | Examine Purchasing Info Record and source list of components                                  | Purchasing          | Manage purchasing info record           | Examine Purchasing Info Record and source list of components                                                   |
|          |                                                                                               |                     |                                         |                                                                                                                |
|          |                                                                                               |                     | Manage source list                      |                                                                                                                |
|          |                                                                                               |                     |                                         |                                                                                                                |
|          |                                                                                               |                     | Manage quota arrangement                |                                                                                                                |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 003      | HC_SAP_DD_MM01_03_Purchasing Info Record and Source List and Quota Arrangement                | Purchasing          | /                                       | Create or Change Purchasing Info Record and source list of components                                          |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 004      | Check MRP views of Component Material Master Data                                             | Purchasing          | MM02/Manage material master data        | Check the MRP views of materials master data. Especially Special procurement type in MRP views and MRP areas.  |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 005      | HC_SAP_DD_PP02_02_MRP Run                                                                     | Planner             | /                                       | Run MRP to generate PR.                                                                                        |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 006      | Need to change PR? (Decision)                                                                 | Procurement         | /                                       | Check the PR info                                                                                              |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 007      | Change PR (if 006=Yes)                                                                        | Procurement         | Process Purchase Requisitions(V2)       | Change PR                                                                                                      |
|          |                                                                                               |                     |                                         |                                                                                                                |
|          |                                                                                               |                     | Mass change Purchase Requisitions       |                                                                                                                |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 008      | Process PR to PO (if 006=No)                                                                  | Procurement         | Process Purchase Requisitions(V2)       | Process PR to PO                                                                                               |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 009      | Manually create PO                                                                            | Procurement         | ME21N/ Manage Purchase Orders - F0842A. | Create PO if need                                                                                              |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 010      | Change/update PO                                                                              | Procurement         | ME22N/Manage Purchase Orders - F0842A.  | Change PO if need                                                                                              |
|          |                                                                                               |                     |                                         |                                                                                                                |
|          |                                                                                               |                     | Mass change Purchase Orders             |                                                                                                                |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 011      | Approved?                                                                                     | Procurement Manager | My inbox                                | Approve the PO                                                                                                 |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 012      | Monitor PO and PO items                                                                       | Procurement         | Manage Purchase Orders - F0842A.        | Display PO                                                                                                     |
|          |                                                                                               |                     |                                         |                                                                                                                |
|          |                                                                                               |                     | Monitor Purchase Order Items (F2358)    | The Monitor Purchase Order Items screen is displayed also; the numbers of current overdue PO items are listed. |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 013      | Create outbound delivery of PO                                                                | Procurement         | VL10B                                   | Create outbound delivery                                                                                       |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 014      | Post goods issue of PO in source plant and Post goods receipts in destination plant meanwhile | Warehouse Admin     | VL02N                                   | Post goods issue and goods receipts.                                                                           |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 015      | Post billing document                                                                         | Planner             | VF01                                    | Post billing document                                                                                          |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 016      | Post goods transfer from plant to MRP area (Optional)                                         | Warehouse Admin     | MIGO                                    | Post goods transfer from plant to MRP area (Optional)                                                          |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 017      | Supplier invoice verification                                                                 | Finance             | MIRO                                    | Supplier invoice verification                                                                                  |
+----------+-----------------------------------------------------------------------------------------------+---------------------+-----------------------------------------+----------------------------------------------------------------------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements-1 .LS_Heading-3}

- For B&S STO, the component master data "Special procurement" = 40 under plant CN7F.

- The vendor (SG21) master data under purchase org R001 should be set the Plant = CN8F

- Info record and source list should be maintained with supply plant=CN8F (SG21) under Plant CN7F.

- Set the material master data "Special procurement code" =45 under CN8F plant MRP area. Then the MRP area demand will be transferred to Plant level.

- When posting goods transfer from CN8F to CN7F subcontractor, the post steps should be two steps. One step is posting goods issue in CN8F, another step is posting goods receipt in CN7F.

- Each buyer will be identified with a buyer code (Purchasing group) in SAP.

- Purchase Requisitions created by MRP will not require approval.

- PO output can be emailed to PO creator, using the email address maintained on the Workforce. The procurement team will download the PO manually and send it to the supplier or add a new output line to maintain supplier email in PO to send it to supplier.

- Vendor list will be maintained as a valid source in SAP (Source List and purchasing Info record).

- The Purchasing team will maintain vendor pricing information.

- All inventory purchases require a 3-way match.

<!-- -->

- Buyers shall be able to specify the following information in each individual PO item:

  - Shipping requirements (shipping conditions).

  - Under- and over-delivery tolerances in each individual PO item.

  - Item-specific texts

<!-- -->

- PO output shall be emailed to Vendors and PO creator as PDF documents, no additional outputs (EDI, XML, Fax, etc.) shall be required.

- Buyers shall be able to manually enter vendors confirmed dates and quantities if needed.

- No electronic receipts of order confirmations or advanced shipping notifications (ASN) are used in the current phase.

- The system allows attachments to all documents in the procurement cycle:

  - Requisitions -- vendor quotes, specs, etc.

  - PO's -- vendor quotes, signed contracts, etc.

  - Goods receipts -- packing list, bill of lading, etc.

<!-- -->

- SAP contract functionality is supported and will not be used in the current phase.

- Materials can be transferred between plants.

- Display vendors performance based on Delivery dates.

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- B&S STOs Purchasing with PR, which is generated by MRP, not require approval.

- B&S STOs Purchasing without PR require approval.

<!-- -->

- The approval process should be applicable to the PO document type ZST2 and Purchasing organization.

- The approval matrix will be further reviewed during the Realize stage.

## Standard Documents / Settings  {#standard-documents-settings-1 .LS_Heading-3}

## Purchase Requisitions {#purchase-requisitions .LS_Heading-3}

  ------------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -----------------------------------
  NB                  Purchase Requisition   Used for Direct procurement items

  ------------------------------------------------------------------------------

## Purchase Orders {#purchase-orders .LS_Heading-3}

  ------------------------------------------------------------------------------------------------------------
  **Document Type**   **Description**                **Comments**
  ------------------- ------------------------------ ---------------------------------------------------------
  ZST1                Stock Transfer Order with PR   Stock Transfer Order with PR, which is generated by MRP

  ZST2                Stock Transfer Order w/o PR    Stock Transfer Order w/o PR
  ------------------------------------------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- Custom POs (ZSTO Doc Type) will be used for stock transfer orders.

- STO release strategies and workflows will be set up to support approvals as defined in section 3.9.

- Custom document number ranges will be used for Purchase orders. [(TBD)]{.mark}

- All inventory materials will have both purchasing and MRP views.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-1 .LS_Heading-3}

- Procurement of direct materials is tightly integrated with other business processes, such as:

  - Materials forecasting and planning.

  - Inventory and warehouse management.

  - Accounting​**​**

## Support / Closing Considerations {#support-closing-considerations-1 .LS_Heading-3}

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

6.  1.  **[KEY APPS]{.smallcaps}**

## Authorization Roles {#authorization-roles-1 .LS_Heading-3}

+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+
| **Business Role**    | **Role Description**                                                        | **Authorization Restrictions** | **Baseline ZRS Role(s)**                       |
+======================+=============================================================================+================================+================================================+
| Planner              | Role includes the following key [system]{.underline} tasks:                 | Std Roles                      | - Z_SAP_BR_MATL_PLNR_EXT_PROC\_Plant           |
|                      |                                                                             |                                |                                                |
|                      | - Execute MRP and monitor results                                           |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Manage MRP data in material master                                        |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Manage planned independent requirements                                   |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Execute material forecast                                                 |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Monitor inventory                                                         |                                |                                                |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+
| Master Data Team     | Role includes the following key [system]{.underline} tasks:                 | Std Roles                      | - Z_SAP_BR_PRODMASTER_SPECIALIST_Plant         |
|                      |                                                                             |                                |                                                |
|                      | - Maintain Business Partner                                                 |                                | - Z_SAP_BR_BUPA_MASTER_SPECIALIST\_CompanyCode |
|                      |                                                                             |                                |                                                |
|                      | - Maintain Product                                                          |                                |                                                |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+
| Purchasing           | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                      | - Z\_ SAP_BR_PURCHASER_Plant                   |
|                      |                                                                             |                                |                                                |
|                      | - Monitor PO status                                                         |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Process PO output on demand                                               |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Manage open PRs                                                           |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Display purchasing master data -- purchasing info records and source list |                                |                                                |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+
| Procurement          | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                      | - Z\_ SAP_BR_PROCUREMENT_Plant                 |
|                      |                                                                             |                                |                                                |
|                      | - Monitor PO status                                                         |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Process PO output on demand                                               |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Manage open PRs                                                           |                                |                                                |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+
| Warehouse Admin      | Role includes the following tasks related to procurement:                   | Std Roles                      | Z_SAP_BR_WAREHOUSE_CLERK_Plant                 |
|                      |                                                                             |                                |                                                |
|                      | - Posting goods receipts, returns                                           |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Document reversal in case of mistakes                                     |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Initiate and process outbound deliveries in case of vendor returns        |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - PO search                                                                 |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Inventory Display                                                         |                                |                                                |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+
| Purchasing Reporting | - Purchasing analytics                                                      | Std Roles Display access.      | - Z_SAP_BR_MASTER_DATA_VIEW_Plant              |
|                      |                                                                             |                                |                                                |
|                      | - All purchasing reports and list displays w/o create/update access         |                                |                                                |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+
| Finance              | - Enter vendor invoices, credit memos                                       | Restricted by company code     |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Post billing document for STO                                             |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Process blocked invoices                                                  |                                |                                                |
|                      |                                                                             |                                |                                                |
|                      | - Process vendor payments                                                   |                                |                                                |
+----------------------+-----------------------------------------------------------------------------+--------------------------------+------------------------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  ----------------------------------------------------------------------------
  **Document Type**            **Document Flow**
  ---------------------------- -----------------------------------------------
  NB -- Standard requisition   MRP - NB requisition\
                               manual entry - NB requisition

  ZST1                         Stock Transfer Order with PR

  ZST2                         Stock Transfer Order w/o PR
  ----------------------------------------------------------------------------

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
| Monitor purchase order items  | List and monitor status of open POs                                                             |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Material Document Overview    | List of materials documents                                                                     |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| supplier invoice list         | - supplier invoice list                                                                         |
+-------------------------------+-------------------------------------------------------------------------------------------------+

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+----------------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                                      |
+---------------------------+---------------------------+----------------+------------------+----------------+---------------------+
| **Report Name**           | **Description**           | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                           |                           |                |                  |                |                     |
|                           |                           |                | **SAP App/Rprt** |                |                     |
+:==========================+:==========================+:===============+:=================+:===============+:====================+
| HC Monthly savings report | HC Monthly savings report |                | /                | High           | ZMM007              |
+---------------------------+---------------------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+----------------------------------------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                                                   |
+-----------------------------------+-----------------------------------+------------------+------------------+--------------------+
| **Interface**                     | **Description**                   | **In Scope**     | **Complexity**   | **Comments**       |
+:==================================+:==================================+:=================+:=================+:===================+
| Mass Change PO item schedule date | Mass Change PO item schedule date |                  |                  | SOS🡪SAP            |
+-----------------------------------+-----------------------------------+------------------+------------------+--------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

范围内需要切换的数据如下

+-----------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                             |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**      | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|               |                   |                           |                            | (# items)**   |                |
+===============+===================+===========================+============================+===============+================+
| N/A           |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+---------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                                                                        |
+--------------------------------------------+--------------------------------------------+------------------+------------------+-------------------------+
| **Enhancement**                            | **Description**                            | **Complexity**   | **In Scope**     | **Comments**            |
+============================================+============================================+==================+==================+:========================+
| custom logic - send email to PO creator    | custom logic - send email to PO creator    | Small            | Yes              |                         |
+--------------------------------------------+--------------------------------------------+------------------+------------------+-------------------------+
| custom logic of cannot change BOM PO price | custom logic of cannot change BOM PO price | Small            | Yes              | For direct procurement  |
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

以下工作流被纳入范围：

+---------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                             |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**      | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| Workflow of ZST2  |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image4.png){width="6.345306211723535in" height="2.3656714785651793in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
