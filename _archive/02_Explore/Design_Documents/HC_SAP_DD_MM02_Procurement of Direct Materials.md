**Procurement of Direct Materials**

**直接采购流程**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****:** **HC_SAP_DD_MM02_Procurement of Direct Materials**

**Version 1.2**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Meos Xu                 MM Lead                08/06/2025
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

[1. Guidelines [7](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [7](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [7](#design-document-approval-options)](#design-document-approval-options)

[2. Risk Order Purchasing [7](#risk-order-purchasing)](#risk-order-purchasing)

[2.1 Purpose [7](#purpose)](#purpose)

[2.2 Business Reason [8](#business-reason)](#business-reason)

[2.3 Business Benefits [8](#business-benefits)](#business-benefits)

[2.4 Purchase Order [8](#purchase-order)](#purchase-order)

[2.5 Business Process for Risk Order Purchasing [9](#business-process-for-risk-order-purchasing)](#business-process-for-risk-order-purchasing)

[▪ Business Process Steps [9](#business-process-steps)](#business-process-steps)

[2.6 HC Functional Requirements [10](#hc-functional-requirements)](#hc-functional-requirements)

[2.7 HC Delegation Of Authority [11](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[2.8 Standard Documents / Settings [11](#standard-documents-settings)](#standard-documents-settings)

[2.8.1 Purchase Requisitions [11](#purchase-requisitions)](#purchase-requisitions)

[2.8.2 Purchase Orders [11](#purchase-orders)](#purchase-orders)

[2.9 Design Considerations / Key Assumptions [12](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[2.10 Cross Functional Integration Dependencies [12](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[2.11 Support / Closing Considerations [12](#support-closing-considerations)](#support-closing-considerations)

[3. Repeating Procurement of Bom Materials [12](#repeating-procurement-of-bom-materials)](#repeating-procurement-of-bom-materials)

[3.1 Purpose [12](#purpose-1)](#purpose-1)

[3.2 Business Reason [12](#business-reason-1)](#business-reason-1)

[3.3 Business Benefits [12](#business-benefits-1)](#business-benefits-1)

[3.4 Planned Independent Requirements and MRP [13](#planned-independent-requirements-and-mrp)](#planned-independent-requirements-and-mrp)

[3.5 Purchase Requisition [13](#purchase-requisition)](#purchase-requisition)

[3.6 Purchase Order [13](#purchase-order-1)](#purchase-order-1)

[3.7 Business Process for Repeating Procurement (Bom Material) [14](#business-process-for-repeating-procurement-bom-material)](#business-process-for-repeating-procurement-bom-material)

[▪ Business Process Steps [14](#business-process-steps-1)](#business-process-steps-1)

[3.8 HC Functional Requirements [15](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[3.9 HC Delegation Of Authority [16](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[3.10 Standard Documents / Settings [16](#standard-documents-settings-1)](#standard-documents-settings-1)

[3.10.1 Purchase Requisitions [16](#purchase-requisitions-1)](#purchase-requisitions-1)

[3.10.2 Purchase Orders [16](#purchase-orders-1)](#purchase-orders-1)

[3.11 Design Considerations / Key Assumptions [16](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[3.12 Cross Functional Integration Dependencies [17](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[3.13 Support / Closing Considerations [17](#support-closing-considerations-1)](#support-closing-considerations-1)

[4. Procurement of CMS&ODM [17](#procurement-of-cmsodm)](#procurement-of-cmsodm)

[4.1 Purpose [17](#purpose-2)](#purpose-2)

[4.2 Business Reason [17](#business-reason-2)](#business-reason-2)

[4.3 Business Benefits [17](#business-benefits-2)](#business-benefits-2)

[4.4 CMS&ODM [17](#cmsodm)](#cmsodm)

[4.5 Purchase Requisition [18](#purchase-requisition-1)](#purchase-requisition-1)

[4.6 Purchase Order [18](#purchase-order-2)](#purchase-order-2)

[4.7 Business Process for Procurement of CMS [19](#business-process-for-procurement-of-cms)](#business-process-for-procurement-of-cms)

[▪ Business Process Steps [20](#business-process-steps-2)](#business-process-steps-2)

[4.8 Business Process for Procurement of ODM [21](#business-process-for-procurement-of-odm)](#business-process-for-procurement-of-odm)

[▪ Business Process Steps [22](#business-process-steps-3)](#business-process-steps-3)

[4.9 HC Functional Requirements [22](#hc-functional-requirements-2)](#hc-functional-requirements-2)

[4.10 HC Delegation Of Authority [23](#hc-delegation-of-authority-2)](#hc-delegation-of-authority-2)

[4.11 Standard Documents / Settings [23](#standard-documents-settings-2)](#standard-documents-settings-2)

[4.11.1 Purchase Requisitions [23](#purchase-requisitions-2)](#purchase-requisitions-2)

[4.11.2 Purchase Orders [23](#purchase-orders-2)](#purchase-orders-2)

[4.12 Design Considerations / Key Assumptions [24](#design-considerations-key-assumptions-2)](#design-considerations-key-assumptions-2)

[4.13 Cross Functional Integration Dependencies [24](#cross-functional-integration-dependencies-2)](#cross-functional-integration-dependencies-2)

[4.14 Support / Closing Considerations [24](#support-closing-considerations-2)](#support-closing-considerations-2)

[5. Invoice Verification [24](#invoice-verification)](#invoice-verification)

[5.1 Purpose [24](#purpose-3)](#purpose-3)

[5.2 Business Reason [25](#business-reason-3)](#business-reason-3)

[5.3 Business Benefits [25](#business-benefits-3)](#business-benefits-3)

[5.4 Business Process for Invoice Verification [26](#business-process-for-invoice-verification)](#business-process-for-invoice-verification)

[▪ Business Process Steps [28](#business-process-steps-4)](#business-process-steps-4)

[5.5 HC Functional Requirements [29](#hc-functional-requirements-3)](#hc-functional-requirements-3)

[5.6 HC Delegation Of Authority [29](#hc-delegation-of-authority-3)](#hc-delegation-of-authority-3)

[5.7 Standard Documents / Settings [29](#standard-documents-settings-3)](#standard-documents-settings-3)

[5.8 Design Considerations / Key Assumptions [29](#design-considerations-key-assumptions-3)](#design-considerations-key-assumptions-3)

[5.9 Cross Functional Integration Dependencies [29](#cross-functional-integration-dependencies-3)](#cross-functional-integration-dependencies-3)

[5.10 Support / Closing Considerations [29](#support-closing-considerations-3)](#support-closing-considerations-3)

[6. Authorization Roles [30](#authorization-roles)](#authorization-roles)

[6.1 Authorization Roles [30](#authorization-roles-1)](#authorization-roles-1)

[7. Document Types and Document Flow [31](#document-types-and-document-flow)](#document-types-and-document-flow)

[8. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [32](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[8.1 Reports [32](#reports)](#reports)

[8.1.1 Standard Reports [32](#standard-reports)](#standard-reports)

[8.1.2 HC Requested Reports [33](#hc-requested-reports)](#hc-requested-reports)

[8.2 Interfaces [33](#interfaces)](#interfaces)

[8.3 Conversions [33](#conversions)](#conversions)

[8.4 Enhancements [34](#enhancements)](#enhancements)

[8.5 Forms [34](#forms)](#forms)

[8.6 Workflows [34](#workflows)](#workflows)

[9. Legend for Process Flow [35](#legend-for-process-flow)](#legend-for-process-flow)

> **\**

**Document Version History**

+:-----------:+:---------------------------------------------------:+:------------------:+
| **Version** | **Summary of Change**                               | **Effective Date** |
+-------------+-----------------------------------------------------+--------------------+
| 1.0         | Create the initial version of the document.         | 08/06/2025         |
+-------------+-----------------------------------------------------+--------------------+
| 1.1         | Add non-BOM risk order process.                     | 08/15/2025         |
|             |                                                     |                    |
|             | Change the preconditions for repeating PO creation. |                    |
|             |                                                     |                    |
|             | Add PO types.                                       |                    |
|             |                                                     |                    |
|             | Split the procurement processes of CMS and ODM      |                    |
+-------------+-----------------------------------------------------+--------------------+
| 1.2         | Change the authorization role                       | 08/22/2025         |
+-------------+-----------------------------------------------------+--------------------+

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

# Risk Order Purchasing {#risk-order-purchasing .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

This process is driven by creating a purchase order for stock able materials. The first decision separates single orders from call-offs. Creating an order might not be difficult for an operative purchaser, because the system knows which kind of order has to be created due to the formerly entered purchasing information.

Orders will be sent in different ways. Sending orders via mail (create printout of order) or email has to be possible.

Prior to order process, purchase info record (PIR) should be maintained already. The PIR provides the option of storing information about a vendor and a material as the master data at purchasing org and plant level. It provides the feasibility as a material may be procured from more than one vendor and the vendor will have different prices, freight costs and terms of delivery.

Purchase order for risk order of new part purchasing should be manually created in system as there is no demand driven from MRP run. Nevertheless, stock needs to be purchased in line with a relevant and authorized request. A PO can be created manually with the document type "Risk Order".

## Business Reason {#business-reason .LS_Heading-3}

Stock materials are procured for new parts of BOM materials and not driving from MRP run.

## Business Benefits {#business-benefits .LS_Heading-3}

- Streamline procurement processes in an efficient and cost-effective manner.

- Ensure highly automated processes for the procurement of direct materials.

- Reduce manual effort greatly.

- Monitor the procurement progress in real-time.

- Use an analytical list page to monitor purchase order items.

## Purchase Order {#purchase-order .LS_Heading-3}

Purchase order is a legal document to request a vendor for a specific material or service under the stated conditions.

In this scope, the purchase orders are all not processed from purchase requisitions.

- **Manually**

<!-- -->

- Purchase Orders can be created manually without Reference

<!-- -->

- **Purchase Order Output**

<!-- -->

- Once Purchase order is approved, the PO details can be communicated to the PO creator.

- Manually download a PDF copy of the purchase order and send it to the supplier.

- Send the PDF copy of purchase order via email manually via add a new output in PO, maintaining the email-id is assigned to the supplier master (BP).

## Business Process for Risk Order Purchasing  {#business-process-for-risk-order-purchasing .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Process Step                                                 | Business Role                   | Transaction/App                                                           | Expected Results                                                                                               |
+==============================================================+=================================+===========================================================================+================================================================================================================+
| 001-Proj Mgr. obtains Risk Order approval                    | Project Manager/Account Manager | Non-SAP                                                                   |                                                                                                                |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 002-If it has master data？                                  | Master Data Team                | Non-SAP                                                                   | If it doesn't have master data, master data team need to create.                                               |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 003-HC_SAP_DD_MM01_01_MM Material Master Data                | Master Data Team                | /                                                                         | Maintain master data                                                                                           |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 004-If it is in BOM?                                         | /                               | /                                                                         | If in BOM, after MRP run purchasing will process PR to PO.                                                     |
|                                                              |                                 |                                                                           |                                                                                                                |
|                                                              |                                 |                                                                           | If not, purchasing need to create PO manually.                                                                 |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 005-HC_SAP_DD_PP02_02_MRP run                                |                                 | /                                                                         | Run MRP                                                                                                        |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 006-Process PR to PO                                         | Purchasing                      | /                                                                         | Process PR to PO                                                                                               |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 007-Create PO                                                | Purchasing                      | ME21N/Manage purchase orders                                              | Create a PO                                                                                                    |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 008-Approved？                                               | Purch.Mgr./Purch. Director      | My inbox                                                                  | Approved.                                                                                                      |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 009-Change/Update PO                                         | Purchasing                      | ME22N/Manage purchase orders                                              | Change PO                                                                                                      |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 010-Monitor PO and PO items                                  | Purchasing                      | Manage Purchase Orders - F0842A.                                          | Display PO                                                                                                     |
|                                                              |                                 |                                                                           |                                                                                                                |
|                                                              |                                 | Monitor Purchase Order Items (F2358)                                      | The Monitor Purchase Order Items screen is displayed also; the numbers of current overdue PO items are listed. |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 011-Print/email to supplier                                  | Purchasing                      | Manage Purchase Orders - F0842A /ME22N Select PO and create a new output. | Print/email                                                                                                    |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 012-HC_SAP_DD_MM07_02_Post Goods Receipts                    | Purchasing                      | /                                                                         | Received and Material doc is created. Inventory updated at S. Loc level                                        |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 013-HC_SAP_DD_MM02_02_Repeating Procurement of Bom Materials | Procurement                     | /                                                                         | Create repeating PO.                                                                                           |
+--------------------------------------------------------------+---------------------------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- Each SE will be identified with a buyer code (Purchasing group) in SAP info record for risk order.

- The field "supplier material group" is also borrowed to maintain SE in info record for risk order.

- Purchase Order created for risk order will require approval as defined by the D.O.A.

- PO output can be emailed to PO creator, using the email address maintained on the Workforce. The procurement team will download the PO manually and send it to the supplier or add a new output line to maintain supplier email in PO to send it to supplier.

- Approved Vendor list will be maintained as a valid source in SAP (Source List and purchasing Info record).

- The Purchasing team will maintain vendor pricing information.

- All inventory purchases require a 3-way match.

<!-- -->

- SE shall be able to specify the following information in each individual PO item:

  - Shipping requirements (shipping conditions).

  - Under- and over-delivery tolerances in each individual PO item.

  - Item-specific texts

<!-- -->

- PO output shall be emailed to Vendors and PO creator as PDF documents, no additional outputs (EDI, XML, Fax, etc.) shall be required.

- SE shall be able to manually enter vendors confirmed dates and quantities if needed.

- No electronic receipts of order confirmations or advanced shipping notifications (ASN) are used in the current phase.

- The system allows attachments to all documents in the procurement cycle:

  - PO's -- vendor quotes, signed contracts, etc.

  - Goods receipts -- packing list, bill of lading, etc.

<!-- -->

- SAP contract functionality is supported and will not be used in the current phase.

- Tax conditions -- Default tax code will be maintained.

- Materials can be transferred between plants.

- A PO can be issued for risk order by SE team.

- Display vendors performance based on Delivery dates.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- Risk Order Purchasing of Bom Materials and not in BOM materials require approval.

- The approval process should be applicable to the PO document type ZR\* and Purchasing organization.

- The approval matrix will be further reviewed during the Realize stage.

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Purchase Requisitions {#purchase-requisitions .LS_Heading-3}

  ------------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -----------------------------------
  NB                  Purchase Requisition   Used for Direct procurement items

  ------------------------------------------------------------------------------

## Purchase Orders {#purchase-orders .LS_Heading-3}

  -------------------------------------------------------------------------
  **Document Type**   **Description**       **Comments**
  ------------------- --------------------- -------------------------------
  ZR1                 Risk order for CN8F   Risk order for CN8F

  ZR2                 Risk order for CN7F   Risk order for CN7F

  ZR3                 Risk order for SG28   Risk order for SG28

  ZR4                 Risk order for CN8C   Risk order for CN8C

  ZR5                 Risk order for CN8B   Risk order for CN8B

  ZR6                 Risk order for CN8E   Risk order for CN8E

  ZR7                 Risk order for CN7B   Risk order for CN7B

  ZR8                 Risk order for US10   Risk order for US10

  ZR9                 Risk order for BE10   Risk order for BE10

  ZR10                Risk order for IN10   Risk order for IN10

  ZR11                Risk order for CN8A   Risk order for CN8A

  ZR12                Risk order for CN7A   Risk order for CN7A

  ZR13                Risk order for CN7C   Risk order for CN7C
  -------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Custom PO types (ZR\* Doc Type) will be used for risk order purchases.

- Custom document number ranges will be used for Purchase orders [(TBD).]{.mark}

- PR/PO release strategies and workflows will be set up to support approvals as defined in section 2.7.

- All inventory materials will have both purchasing and MRP views.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Procurement of direct materials is tightly integrated with other business processes, such as:

  - Materials forecasting and planning.

  - Inventory and warehouse management.

  - Accounting​**​**

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# Repeating Procurement of Bom Materials {#repeating-procurement-of-bom-materials .LS_Heading-1}

3.  

<!-- -->

2.  

## Purpose {#purpose-1 .LS_Heading-3}

This purchasing process uses purchase requisitions that are generated either by the Material Requirements Planning (MRP) process. The conversion from a purchase requisition to a purchase order can either be done manually (in case adoptions are necessary) or automatically (applicable for large volumes).

In general, requisitions for Direct Materials will not require approval. Goods are shipped from the supplier and the goods receipt is created with reference to the corresponding purchase order. Subsequently the invoicing process is triggered. The user can monitor the progress throughout the entire procurement process and can initiate reactive actions if needed.

## Business Reason {#business-reason-1 .LS_Heading-3}

Material is procured from a vendor.

## Business Benefits {#business-benefits-1 .LS_Heading-3}

- Streamline procurement processes in an efficient and cost-effective manner.

- Ensure highly automated processes for the procurement of direct materials.

- Reduce manual effort greatly.

- Monitor the procurement progress in real-time.

- Use an analytical list page to monitor purchase order items.

## Planned Independent Requirements and MRP {#planned-independent-requirements-and-mrp .LS_Heading-3}

A Planned Independent Requirement is a planned requirement for a material and a supply planning area without reference to a sales order. It contains a time series with the planned material requirements (Planned Independent Requirement items) and identifying and administrative information.

The requirement/demand for the product (finished) is generated either through Planned Independent Requirement or through Sales Order and dependent requirement is generated by the system once the MRP run is taken place based on their stocks availability during the Material Requirement Planning (MRP) run.

Material requirements planning will run periodically as scheduled to create supply elements for all existing demands. MRP creates a supply element if the expected supply is less than the expected demand on a certain date.

Material requirements planning will run periodically as scheduled to create supply elements for all.

## Purchase Requisition  {#purchase-requisition .LS_Heading-3}

Purchase Requisition is an internal Document instructing the purchasing department to request a specific good or service for a specified time.

In this scope, Purchase Requisitions can be created in one way:

- **Automatically**

<!-- -->

- MRP uses Purchasing Requisition document type NB.

- The supplier is copied from the Purchasing Info-record (Auto Srv is activated).

## Purchase Order {#purchase-order-1 .LS_Heading-3}

Purchase order is a legal document to request a vendor for a specific material or service under the stated conditions.

In this scope, the purchase orders are all processed from purchase requisitions.

- **Manually**

<!-- -->

- With reference to Purchase Requisition

<!-- -->

- **Purchase Order Output**

<!-- -->

- Once Purchase order is approved, the PO details can be communicated to the PO creator.

- Manually download a PDF copy of the purchase order and send it to the supplier.

- Send the PDF copy of purchase order via email manually via add a new output in PO, provided the email-id is assigned to the supplier master (BP).

## Business Process for Repeating Procurement (Bom Material)  {#business-process-for-repeating-procurement-bom-material .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Process Step                                           | Business Role | Transaction/App                                                           | Expected Results                                                                                               |
+========================================================+===============+===========================================================================+================================================================================================================+
| 001-HC_SAP_DD_PP02_02_MRP Pun                          | Planner       | /                                                                         | MRP run and generate PR.                                                                                       |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 002- Is the purchasing group for PR SE or Procurement? | /             | /                                                                         | Check if the purchasing group for PR is SE or Procurement.                                                     |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 003-HC_SAP_DD_MM06_01\_                                | Purchasing    | /                                                                         | Create Risk order                                                                                              |
|                                                        |               |                                                                           |                                                                                                                |
| Purchasing for Risk Order                              |               |                                                                           |                                                                                                                |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 004-Need to change PR?                                 | Procurement   | No-SAP                                                                    | Check if the PR need to be changed.                                                                            |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 005-Change PR                                          | Procurement   | Process Purchase Requisitions(V2)                                         | Change PR.                                                                                                     |
|                                                        |               |                                                                           |                                                                                                                |
|                                                        |               | Mass change Purchase Requisitions                                         |                                                                                                                |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 006-Change/update PO                                   | Procurement   | Manage Purchase Orders - F0842A.                                          | Change PO                                                                                                      |
|                                                        |               |                                                                           |                                                                                                                |
|                                                        |               | Mass change Purchase Orders                                               |                                                                                                                |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 007-Process PR to PO                                   | Procurement   | Process Purchase Requisitions(V2)                                         | Manually process PR to PO.                                                                                     |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 008-Monitor PO and PO items                            | Procurement   | Manage Purchase Orders - F0842A.                                          | Display PO                                                                                                     |
|                                                        |               |                                                                           |                                                                                                                |
|                                                        |               | Monitor Purchase Order Items (F2358)                                      | The Monitor Purchase Order Items screen is displayed also; the numbers of current overdue PO items are listed. |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 009-Print/email to supplier                            | Procurement   | Manage Purchase Orders - F0842A /ME22N Select PO and create a new output. | Print/email                                                                                                    |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| 010-HC_SAP_DD_MM07_02_Post Goods receipts              | Procurement   | /                                                                         | Received and Material doc is created. Inventory updated at S. Loc level                                        |
+--------------------------------------------------------+---------------+---------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements-1 .LS_Heading-3}

- The price in the Purchase Order (PO) should be retrieved from the Info Record based on the scheduled delivery date when creating PO.

- The price of purchase order changing when info record changing need to discuss in realize stage.

- Each buyer will be identified with a buyer code (Purchasing group) in SAP for repeating procurement.

- Purchase Requisitions created by MRP will not require approval.

- Purchase Orders for repeating procurement will not require approval.

- PO output can be emailed to PO creator, using the email address maintained on the Workforce. The procurement team will download the PO manually and send it to the supplier or add a new output line to maintain supplier email in PO to send it to supplier.

- Approved Vendor list will be maintained as a valid source in SAP (Source List and purchasing Info record).

- The Purchasing team will maintain vendor pricing information.

- All inventory purchases require a 3-way match.

<!-- -->

- Buyers shall be able to specify the following information in each individual PO item:

  - Shipping requirements (shipping conditions).

  - Under- and over-delivery tolerances in each individual PO item.

  - Item-specific texts

<!-- -->

- PO output shall be emailed to Vendors and PO creator as PDF documents, no additional outputs (EDI, XML, Fax, etc.) shall be required.

- Buyers shall be able to manually enter vendors confirmed delivery dates and quantities if needed.

- No electronic receipts of order confirmations or advanced shipping notifications (ASN) are used in the current phase.

- The system allows attachments to all documents in the procurement cycle:

  - Requisitions -- vendor quotes, specs, etc.

  - PO's -- vendor quotes, signed contracts, etc.

  - Goods receipts -- packing list, bill of lading, etc.

<!-- -->

- SAP contract functionality is supported and will not be used in the current phase.

- Tax conditions -- Default tax code will be maintained in info record.

- Materials can be transferred between plants.

- A repeating PO should not be issued, if that vendor is not yet created.

- Display vendors performance based on Delivery dates.

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- Direct Materials Purchase requisitions from MRP do not require approval.

## Standard Documents / Settings  {#standard-documents-settings-1 .LS_Heading-3}

## Purchase Requisitions {#purchase-requisitions-1 .LS_Heading-3}

  ------------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -----------------------------------
  NB                  Purchase Requisition   Used for Direct procurement items

  ------------------------------------------------------------------------------

## Purchase Orders {#purchase-orders-1 .LS_Heading-3}

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

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- Custom PO types (ZN\* Doc Type) will be used for direct materials purchases.

- Custom document number ranges will be used for Purchase orders. [(TBD)]{.mark}

- All inventory materials will have both purchasing and MRP views.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-1 .LS_Heading-3}

- Procurement of direct materials is tightly integrated with other business processes, such as:

  - Materials forecasting and planning.

  - Inventory and warehouse management.

  - Accounting​**​**

## Support / Closing Considerations {#support-closing-considerations-1 .LS_Heading-3}

- N/A

# Procurement of CMS&ODM {#procurement-of-cmsodm .LS_Heading-1}

4.  

<!-- -->

3.  

## Purpose {#purpose-2 .LS_Heading-3}

This purchasing process uses purchase requisitions for CMS&ODM that are generated by the Material Requirements Planning (MRP) process. The conversion from a purchase requisition to a purchase order can either be done manually (in case adoptions are necessary) or automatically (applicable for large volumes).

In general, requisitions for CMS&ODM will not require approval. Goods are shipped from the supplier and the goods receipt is created with reference to the corresponding purchase order. Subsequently the invoicing process is triggered. The user can monitor the progress throughout the entire procurement process and can initiate reactive actions if needed.

## Business Reason {#business-reason-2 .LS_Heading-3}

Material is procured for CMS&ODM.

## Business Benefits {#business-benefits-2 .LS_Heading-3}

- Streamline procurement processes in an efficient and cost-effective manner.

- Ensure highly automated processes for the procurement of direct materials.

- Reduce manual effort greatly.

- Monitor the procurement progress in real-time.

- Use an analytical list page to monitor purchase order items.

## CMS&ODM {#cmsodm .LS_Heading-3}

CMS refers to Contract Manufacturing. Implication is outsourcing manufacturing services with key parts sold by Home Control.

ODM refers to Original Design Manufacturer (ODM). Implication is buying Finished product as per specifications and selling to customer.

From SAP perspective, the flow is made up of standard sales and purchasing. Purchase order (ZN\*) will be adopted for this purchasing portion in the scenario.

In principle, the flow for raw material is buying from external vendor and selling to ODM/CMS customer. For finished goods flow, this is started from buying from ODM/CMS vendor and selling to external customer.

In Home Controls, coverage of ODM/CMS business applies to raw material and finished goods.

Under Singapore ODM/CMS plant CN8B, all of those variants have been extended.

Under China ODM/CMS plant CN7B, Raw material ODM is not inclusive.

## Purchase Requisition  {#purchase-requisition-1 .LS_Heading-3}

Purchase Requisition is an internal Document instructing the purchasing department to request a specific good or service for a specified time.

In this scope, Purchase Requisitions are always created in one way:

- **Automatically**

<!-- -->

- MRP uses Purchasing Requisition document type NB.

- The supplier is copied from the Purchasing Info-record (Auto Srv is activated).

## Purchase Order {#purchase-order-2 .LS_Heading-3}

Purchase order is a legal document to request a vendor for a specific material or service under the stated conditions.

In this scope, the purchase orders are all processed from purchase requisitions.

- **Manually**

<!-- -->

- With reference to Purchase Requisition

<!-- -->

- **Purchase Order Output**

<!-- -->

- Once Purchase order is approved, the PO details can be communicated to the PO creator.

- Manually download a PDF copy of the purchase order and send it to the supplier.

- Send the PDF copy of purchase order via email manually via add a new output in PO, provided the email-id is assigned to the supplier master (BP).

## Business Process for Procurement of CMS  {#business-process-for-procurement-of-cms .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Process Step                                                             Business Role     Transaction/App                     Expected Results
  ------------------------------------------------------------------------ ----------------- ----------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------
  001-Submit Purchase Order/Forecast Demand                                Customers         Non-SAP                             Customer demand

  002-Create Sales Contract                                                Sales Planner     Manage sales contract               Create Sales Contract

  003-Create Long Time Planning                                            Sales Planner     Manage PIR                          Create Long Time Planning

  004-Create Sales Order                                                   Sales Planner     Manage sales order/VA01             Create Sales Order

  005-HC_SAP_DD_PP02_02_MRP Run                                            Sales Planner     /                                   MRP run to generate PR

  006-Process PR to PO                                                     Procurement       Process Purchase Requisitions(V2)   Process PR to PO

  007-is component or finished goods                                       Procurement       /                                   Check if is component or finished goods. If it is for FG, CMS vendor needs to manufacture, otherwise, CMS vendor needs to create PO to Home Control.

  008-Create Sales Order for finished goods to Home Control                CMS Vendor        Non-SAP                             

  009- Create purchase order for material to Home Control                  CMS Vendor        Non-SAP                             CMS vendor needs to create purchase order to Home Control

  010-Produce materials and send to Home Control                           Material Vendor   Non-SAP                             Material vendor needs to produce materials

  011-Post good receipt, produce finished goods and send to Home Control   CMS Vendor        /                                   

  012-HC_SAP_DD_MM07_02_Good Receipt                                       Warehouse Admin   /                                   Post goods receipt for FG or components

  013-HC_SAP_DD_SD03_Delivery Processing                                   Sales Planner     /                                   Post goods issue for FG to customer or components to vendor.

  014-HC_SAP_DD_SD04_01_Billing Process                                    Sales Planner     /                                   Billing for FG to customer or components to vendor.

  015-is component or finished goods                                       /                 /                                   If it is component, CMS vendor needs to manufacture.
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Business Process for Procurement of ODM  {#business-process-for-procurement-of-odm .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Process Step                                          Business Role     Transaction/App                     Expected Results
  ----------------------------------------------------- ----------------- ----------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------
  001-Submit Purchase Order/Forecast Demand             Customers         Non-SAP                             Customer demand

  002-Create Sales Contract                             Sales Planner     Manage sales contract               Create Sales Contract

  003-Create Long Time Planning                         Sales Planner     Manage PIR                          Create Long Time Planning

  004-Create Sales Order                                Sales Planner     Manage sales order/VA01             Create Sales Order

  005-HC_SAP_DD_PP02_02_MRP Run                         Sales Planner     /                                   MRP run to generate PR

  006-Process PR to PO                                  Procurement       Process Purchase Requisitions(V2)   Process PR to PO

  007-is component or finished goods                    Procurement       /                                   Check if is component or finished goods. If it is for FG, ODM Vendor need to manufacture, otherwise, material vendor need to do this.

  008-Produce finished goods and send to Home Control   ODM vendor        Non-SAP                             

  009- Produce materials and send to Home Control       material vendor   Non-SAP                             

  010-HC_SAP_DD_MM07_02_Good Receipt                    Warehouse Admin   /                                   Post goods receipt for FG or components

  011-HC_SAP_DD_SD03_Delivery Processing                Sales Planner     /                                   Post goods issue for FG to customer or components to vendor.

  012-HC_SAP_DD_SD04_01_Billing Process                 Sales Planner     /                                   Billing for FG to customer or components to vendor.
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements-2 .LS_Heading-3}

- Each buyer will be identified with a buyer code (Purchasing group) in SAP.

- Purchase Requisitions created by MRP will not require approval.

- PO output can be emailed to PO creator, using the email address maintained on the Workforce. The procurement team will download the PO manually and send it to the supplier or add a new output line to maintain supplier email in PO to send it to supplier.

- Approved Vendor list will be maintained as a valid source in SAP (Source List and purchasing Info record).

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

- Tax conditions -- Default tax code will be maintained.

- Materials can be transferred between plants.

- Display vendors performance based on Delivery dates.

## HC Delegation Of Authority {#hc-delegation-of-authority-2 .LS_Heading-3}

- CMS&ODM Materials Purchase requisitions from MRP do not require approval.

## Standard Documents / Settings  {#standard-documents-settings-2 .LS_Heading-3}

## Purchase Requisitions {#purchase-requisitions-2 .LS_Heading-3}

  ------------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -----------------------------------
  NB                  Purchase Requisition   Used for Direct procurement items

  ------------------------------------------------------------------------------

## Purchase Orders {#purchase-orders-2 .LS_Heading-3}

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

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-2 .LS_Heading-3}

- Standard POs (ZN\* Doc Type) will be used for direct materials purchases.

- Custom document number ranges will be used for Purchase orders. [(TBD)]{.mark}

- All inventory materials will have both purchasing and MRP views.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-2 .LS_Heading-3}

- Procurement of CMS&ODM materials is tightly integrated with other business processes, such as:

  - Materials forecasting and planning.

  - Inventory and warehouse management.

  - Accounting​**​**

## Support / Closing Considerations {#support-closing-considerations-2 .LS_Heading-3}

- N/A

# Invoice Verification {#invoice-verification .LS_Heading-1}

5.  

<!-- -->

4.  

## Purpose {#purpose-3 .LS_Heading-3}

Logistics Invoice Verification (LIV) is part of material management. At the end of logistics chain comprising purchasing, inventory management and invoice verification. LIV checks incoming invoices for accuracy with regards to content, price, and accounting.

Main task of LIV is to complete the procedure of materials procurement by posting the vendor invoice and pass on information concerning the invoice to Financial Accounting and subsequent application.

ERS standards for Evaluated Receipt Settlement. Procedure for settling goods receipts automatically. When you use Evaluated Receipt Settlement (ERS), you agree with the vendor that the latter will not submit an invoice in respect of a purchase order transaction. Instead, the system posts the invoice document automatically on the basis of the data in the purchase order and goods receipts. This eliminates invoice variances.

Standard process of LIV has been implemented in Home Control.

Invoice will be validated with quantity variance and price variance. Warehouse should cooperate to clear the variance if which is due to inaccurate GR quantity.

In order to provide the traceability in system, invoices which with price variance should be post in SAP and undertake the check. Block will be automatically placed on the invoices with variance. Those should apply for the approval from purchasing manager and release action can only be performed when the approval is granted. Those rejected should be reverse from system.

Partial of vendors accept the ERS term whereas Home Control will adopt the price from PO and confirm with their payment on monthly basis. The information will be extracted from system and download into a list via bespoke program.

## Business Reason {#business-reason-3 .LS_Heading-3}

Invoice verification after posting goods receipts.

## Business Benefits {#business-benefits-3 .LS_Heading-3}

- Close purchasing transactions quickly

- Avoid communication errors

- Eliminate price and quantity variances in invoice verification

- Streamlined procurement processes in an efficient and cost-effective manner

- Ensure highly automated processes

- Reduce manual effort greatly

- View analytical list page: Monitor purchase order items

## Business Process for Invoice Verification {#business-process-for-invoice-verification .LS_Heading-3}

## ![](media/media/image6.emf) {#section .LS_Heading-3}

## Business Process Steps {#business-process-steps-4 .LS_Heading-3}

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Process Step                                                        Business Role            Transaction/App                                     Expected Results
  ------------------------------------------------------------------- ------------------------ --------------------------------------------------- ---------------------------------------------------------------
  001-HC_SAP_DD_MM07_02_Good Receipt                                  Warehouse Admin          /                                                   Post goods receipts

  002-Inform Purchasing/Procurement for GR completion                 Warehouse Admin          Non-SAP                                             

  003-Is ERS？                                                        AP Admin                 Non-SAP                                             Check if it is ERS.

  004-Submission of invoice from vendor                               AP Admin                 Non-SAP                                             Get the invoice

  005-Has quantity difference？                                       AP Admin                 Non-SAP                                             Check if has quantity difference.

  006-Reverse Goods Receipt Document and Post with correct quantity   AP Admin                 MIGO                                                Reverse Goods Receipt Document and Post with correct quantity

  007-Invoice Verification                                            AP Admin                 MIRO/supplier invoice list                          

  008Has price difference?                                            AP Admin                 Non-SAP                                             

  009-Display Blocked Invoice                                         AP Admin                 MIRO/ supplier invoice list                         Display Blocked Invoice

  009A-SE rectify & Send to Purchasing Manager for Approval           Purchasing/Procurement   Non-SAP                                             SE rectify & Send to Purchasing Manager for Approval

  009B- Vendor issue credit/debit note?                               AP Admin                 Non-SAP                                             

  009C-Invoice Reversal                                               AP Admin                 MR8M/supplier invoice list                          Invoice Reversal

  009D- Approved?                                                     Purchasing Manager       Non-SAP                                             

  009E-Release Blocked Invoice                                        AP Admin                 MRBR                                                Release Blocked Invoice

  010-Display Vendor Line Report                                      AP Admin                 Manage Supplier Line Items                          Display the journal entry.

  011-Display Account Balance                                         AP Admin                 Display G/L Account Balances                        Display the journal entry and account balance

  012-Generate Invoice Evaluated Receipt Settlement                   AP Admin                 Schedule Supplier Invoice Jobs -- Advanced(F1683)   

  013-Discrepancy?                                                    AP Admin                 Non-SAP                                             

  013A-Price Different?                                               AP Admin                 Non-SAP                                             

  013B-Quantity Different                                             AP Admin                 Non-SAP                                             

  013C-Send to respective SE for rectification                        AP Admin                 Non-SAP                                             

  013D-Send to SE for notification                                    AP Admin                 Non-SAP                                             
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements-3 .LS_Heading-3}

- All inventory purchases require a 3-way match.

<!-- -->

- Buyers shall be able to specify the following information in each individual PO item:

  - Shipping requirements (shipping conditions).

  - Under- and over-delivery tolerances in each individual PO item.

  - Item-specific texts

<!-- -->

- Tax conditions -- Default tax code will be maintained.

## HC Delegation Of Authority {#hc-delegation-of-authority-3 .LS_Heading-3}

- The approval is out of SAP.

## Standard Documents / Settings  {#standard-documents-settings-3 .LS_Heading-3}

N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-3 .LS_Heading-3}

N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-3 .LS_Heading-3}

- Procurement of direct materials is tightly integrated with other business processes, such as:

  - Materials forecasting and planning.

  - Inventory and warehouse management.

  - Accounting​**​**

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

+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| **Business Role**               | **Role Description**                                                        | **Authorization Restrictions**                                                                             | **Baseline ZRS Role(s)**                       |
+=================================+=============================================================================+============================================================================================================+================================================+
| Planner                         | Role includes the following key [system]{.underline} tasks:                 | Std Roles                                                                                                  | - Z_SAP_BR_MATL_PLNR_EXT_PROC_CompanyCode      |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Execute MRP and monitor results                                           |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Manage MRP data in material master                                        |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Manage planned independent requirements                                   |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Execute material forecast                                                 |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Monitor inventory                                                         |                                                                                                            |                                                |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| Master Data Team                | Role includes the following key [system]{.underline} tasks:                 | Std Roles                                                                                                  | - Z_SAP_BR_PRODMASTER_SPECIALIST\_CompanyCode  |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Maintain Business Partner                                                 |                                                                                                            | - Z_SAP_BR_BUPA_MASTER_SPECIALIST\_CompanyCode |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Maintain Product                                                          |                                                                                                            |                                                |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| Purchasing                      | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                                                                                                  | - Z\_ SAP_BR_PURCHASER_CompanyCode             |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Monitor PO status                                                         | Can only view risk orders, STOs and inderict orders(purchase orders are distinguished by order type)       |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Process PO output on demand                                               |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Manage open PRs                                                           |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Display purchasing master data -- purchasing info records and source list |                                                                                                            |                                                |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| Procurement                     | - Manage POs (create, change, cancel, display) and Contracts                | Std Roles                                                                                                  | - Z\_ SAP_BR_PROCUREMENT_CompanyCode           |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Monitor PO status                                                         | Can only view repeating orders, STOs and inderict orders (purchase orders are distinguished by order type) |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Process PO output on demand                                               |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Manage open PRs                                                           |                                                                                                            |                                                |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| Purchasing manager /PO Approver | - Display and approve POs                                                   | Std Roles                                                                                                  | - Z_SAP_BR_PURCHASING_MANAGER_CompanyCode      |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| Warehouse Admin                 | Role includes the following tasks related to procurement:                   | Std Roles                                                                                                  | Z_SAP_BR_WAREHOUSE_CLERK_CompanyCode           |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Posting goods receipts, returns                                           |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Document reversal in case of mistakes                                     |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Initiate and process outbound deliveries in case of vendor returns        |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - PO search                                                                 |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Inventory Display                                                         |                                                                                                            |                                                |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| Purchasing Reporting            | - Purchasing analytics                                                      | Std Roles Display access.                                                                                  | - Z_SAP_BR_MASTER_DATA_VIEW_CompanyCode        |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - All purchasing reports and list displays w/o create/update access         |                                                                                                            |                                                |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+
| Accounts Payable Accountant     | - Enter vendor invoices, credit memos                                       | Restricted by company code                                                                                 | - Z\_ SAP_BR_AP_ACCOUNTANT_CompanyCode         |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Process blocked invoices                                                  |                                                                                                            |                                                |
|                                 |                                                                             |                                                                                                            |                                                |
|                                 | - Process vendor payments                                                   |                                                                                                            |                                                |
+---------------------------------+-----------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  ----------------------------------------------------------------------------
  **Document Type**            **Document Flow**
  ---------------------------- -----------------------------------------------
  NB -- Standard requisition   MRP - NB requisition\
                               manual entry - NB requisition

  ZR1                          Risk order for CN8F

  ZR2                          Risk order for CN7F

  ZR3                          Risk order for SG28

  ZR4                          Risk order for CN8C

  ZR5                          Risk order for CN8B

  ZR6                          Risk order for CN8E

  ZR7                          Risk order for CN7B

  ZR8                          Risk order for US10

  ZR9                          Risk order for BE10

  ZR10                         Risk order for IN10

  ZR11                         Risk order for CN8A

  ZR12                         Risk order for CN7A

  ZR13                         Risk order for CN7C

  ZN1                          Repeating Procurement for CN8F

  ZN2                          Repeating Procurement for CN7F

  ZN3                          Repeating Procurement for SG28

  ZN4                          Repeating Procurement for CN8C

  ZN5                          Repeating Procurement for CN8B

  ZN6                          Repeating Procurement for CN8E

  ZN7                          Repeating Procurement for CN7B

  ZN8                          Repeating Procurement for US10

  ZN9                          Repeating Procurement for BE10

  ZN10                         Repeating Procurement for IN10

  ZN11                         Repeating Procurement for CN8A

  ZN12                         Repeating Procurement for CN7A

  ZN13                         Repeating Procurement for CN7C
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
|                               | - PR to PO cycle time                                                                           |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| supplier invoice list         | - supplier invoice list                                                                         |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Manage Supplier Line Items    | - Manage Supplier Line Items                                                                    |
+-------------------------------+-------------------------------------------------------------------------------------------------+
| Display G/L Account Balances  | - Display G/L Account Balances                                                                  |
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
| Open Pos      | SAP ECC           | Low                       | Med                        | TBD           |                |
|               |                   |                           |                            |               |                |
| 未清PO        |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|               |                   |                           |                            |               |                |
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

+------------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                                |
+----------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**         | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+======================+===================+===================+===================+===================+
| PO Approval Workflow | Approvers are TBD | Med               | Yes               | For risk order    |
+----------------------+-------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image7.png){width="6.345306211723535in" height="2.3656714785651793in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
