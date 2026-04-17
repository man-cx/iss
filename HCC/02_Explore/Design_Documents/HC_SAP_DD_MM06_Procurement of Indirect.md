**Procurement of Indirect**

**间接采购流程**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_MM06\_****Procurement of Indirect**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Meos Xu                 MM Lead                08/07/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Rocky Cai            Project Manager        

      Jelly Ding              Purchasing          

     Yu Xiaodong              Purchasing          

      Cherry Qu               Purchasing          

      Sally Jin           Finance - AP/cash       

     Minting Wang              Finance            

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [5](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [5](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. Purchasing for Service [5](#purchasing-for-service)](#purchasing-for-service)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [6](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[2.4 Business Process for Purchasing for Service [7](#business-process-for-purchasing-for-service)](#business-process-for-purchasing-for-service)

[▪ Business Process Steps [7](#business-process-steps)](#business-process-steps)

[2.5 HC Functional Requirements [8](#hc-functional-requirements)](#hc-functional-requirements)

[2.6 HC Delegation Of Authority [9](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[2.7 Standard Documents / Settings [9](#standard-documents-settings)](#standard-documents-settings)

[2.7.1 Purchase Requisitions [9](#purchase-requisitions)](#purchase-requisitions)

[2.7.2 Purchase Orders [9](#purchase-orders)](#purchase-orders)

[2.7.3 Account Assignment Category [(TBD in Realize Stage)]{.mark} [9](#account-assignment-category-tbd-in-realize-stage)](#account-assignment-category-tbd-in-realize-stage)

[2.7.4 Price Condition [9](#price-condition)](#price-condition)

[2.7.5 Purchasing Organization of NPR in CN13&CN17 [9](#purchasing-organization-of-npr-in-cn13cn17)](#purchasing-organization-of-npr-in-cn13cn17)

[2.8 Design Considerations / Key Assumptions [9](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[2.9 Cross Functional Integration Dependencies [10](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[2.10 Support / Closing Considerations [10](#support-closing-considerations)](#support-closing-considerations)

[3. Purchasing for Fixed Asset and Asset Under Construction [10](#purchasing-for-fixed-asset-and-asset-under-construction)](#purchasing-for-fixed-asset-and-asset-under-construction)

[3.1 Purpose [10](#purpose-1)](#purpose-1)

[3.2 Business Reason [10](#business-reason-1)](#business-reason-1)

[3.3 Business Benefits [10](#business-benefits-1)](#business-benefits-1)

[3.4 Business Process for Fixed Asset and Asset Under Construction [11](#business-process-for-fixed-asset-and-asset-under-construction)](#business-process-for-fixed-asset-and-asset-under-construction)

[▪ Business Process Steps [11](#business-process-steps-1)](#business-process-steps-1)

[3.5 HC Functional Requirements [12](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[3.6 HC Delegation Of Authority [13](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[3.7 Standard Documents / Settings [13](#standard-documents-settings-1)](#standard-documents-settings-1)

[3.7.1 Purchase Requisitions [13](#purchase-requisitions-1)](#purchase-requisitions-1)

[3.7.2 Purchase Orders [13](#purchase-orders-1)](#purchase-orders-1)

[3.7.3 Account Assignment Category[(TBD in Realize Stage)]{.mark} [13](#account-assignment-categorytbd-in-realize-stage)](#account-assignment-categorytbd-in-realize-stage)

[3.7.4 Price Condition [13](#price-condition-1)](#price-condition-1)

[3.7.5 Purchasing Organization of NPR in CN13&CN17 [13](#purchasing-organization-of-npr-in-cn13cn17-1)](#purchasing-organization-of-npr-in-cn13cn17-1)

[3.8 Design Considerations / Key Assumptions [14](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[3.9 Cross Functional Integration Dependencies [14](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[3.10 Support / Closing Considerations [14](#support-closing-considerations-1)](#support-closing-considerations-1)

[4. Authorization Roles [14](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [14](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [15](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [15](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [15](#reports)](#reports)

[6.1.1 Standard Reports [15](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [16](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [16](#interfaces)](#interfaces)

[6.3 Conversions [17](#conversions)](#conversions)

[6.4 Enhancements [17](#enhancements)](#enhancements)

[6.5 Forms [17](#forms)](#forms)

[6.6 Workflows [17](#workflows)](#workflows)

[7. Legend for Process Flow [18](#legend-for-process-flow)](#legend-for-process-flow)

> **\**

**Document Version History**

  ------------- -------------------------------------------------------- --------------------
   **Version**                   **Summary of Change**                    **Effective Date**

       1.0            Create the initial version of the document.             08/07/2025

       1.1         Add the processing for adding tax-inclusive prices         08/13/2025

       1.2       Change process as comments, e.g. 3-way or 2-way match.       08/15/2025
  ------------- -------------------------------------------------------- --------------------

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

# Purchasing for Service {#purchasing-for-service .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

This scope item contains the creation and approval of purchase orders for services. This process can also be triggered via the creation of a purchase requisition, which is later converted to a purchase order. The service fulfilment can be steered and monitored with the service entry sheet. Afterwards, the invoicing process is triggered.

## Business Reason {#business-reason .LS_Heading-3}

Purchasing for service.

## Business Benefits {#business-benefits .LS_Heading-3}

- Provide efficient and cost-effective streamlined procurement processes

- Ensure highly automated processes for the procurement of service

- Reduce manual effort greatly

- Monitor the service fulfillment in real time

- Monitor purchase order items with analytical list page

## Business Process for Purchasing for Service {#business-process-for-purchasing-for-service .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| **Step** | **Step Name**                              | **Role**                  | **SAP App Name**                            | **Expected Results**                                                                                        |
+==========+============================================+===========================+=============================================+=============================================================================================================+
| 001      | Create PR                                  | Requester                 | My Purchase Requisitions - New              | Create service PR with Acct Assignment Category for cost center or project.                                 |
|          |                                            |                           |                                             |                                                                                                             |
|          |                                            |                           |                                             | If need to confirm service entry sheets, you need to choose "02- Service" in the field "Product Type Group" |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 002      | Approved PR?                               | Approver                  | My Inbox - All Items                        | Approve the PR                                                                                              |
|          |                                            |                           |                                             |                                                                                                             |
|          |                                            |                           |                                             | Xiaodong is an approver of the workflow to add attachment.                                                  |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 003      | change PR                                  | Requester                 | My Purchase Requisitions - New              | When PR is rejected, you can change PR to retrigger approval.                                               |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 004      | Process PR to PO                           | Purchasing                | Process Purchase Requisitions (V2) (F1048A) | Process PR to PO                                                                                            |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 005      | Approved PO?                               | Func. Mgr./ Pur. Director | My Inbox - All Items                        | Approve the PO                                                                                              |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 006      | Print PO                                   | Purchasing                | ME22N/Manage Purchase Orders                | Print PO if need.                                                                                           |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 007      | Send PO to vendor                          | Purchasing                | ME22N/Manage Purchase Orders                | Send PO to vendor if need.                                                                                  |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 008      | Needs to confirm service or goods receipt? | Purchasing                | /                                           | Check if need to confirm service or goods receipt.                                                          |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 009      | Confirm Service Received                   | Requester                 | Manage Service Entry Sheets - Lean Services | Confirm service entry sheet.                                                                                |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| 010      | HC_SAP_DD_MM02_04_Invoice Verification     | AP admin                  | /                                           | Invoice verification.                                                                                       |
+----------+--------------------------------------------+---------------------------+---------------------------------------------+-------------------------------------------------------------------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- Purchase Requisition created for indirect will require approval as defined by the D.O.A.

- Create service PR with Acct Assignment Category for cost center or project or others.

  - If need to confirm service entry sheets, requester need to choose "02- Service" in the field "Product Type Group.

- Purchase Order created for indirect will require approval as defined by the D.O.A.

- For indirect procurement under CN13/CN17, the purchase order (PO) shall include the tax-inclusive price, with the tax rate and tax condition type (ZTAX) set. After entering the price in the PO line item, the PO line item will display the tax-exclusive price, while the pricing conditions will show the tax-inclusive price, tax rate and tax-exclusive price.

- For indirect procurement under CN13/CN17, we need to use a purchasing organization R003.

- PO output can be emailed to PO creator, using the email address maintained on the Workforce. The procurement team will download the PO manually and send it to the supplier or add a new output line to maintain supplier email in PO to send it to supplier.

- Some of the indirect purchases require 3-way match and some require 2-way match. It depends on Acct Assignment Category.

<!-- -->

- PO output shall be emailed to Vendors and PO creator as PDF documents, no additional outputs (EDI, XML, Fax, etc.) shall be required.

- The system allows attachments to all documents in the procurement cycle:

  - PO's -- vendor quotes, signed contracts, etc.

<!-- -->

- SAP contract functionality is supported and will not be used in the current phase.

- Tax conditions -- Default tax code will be maintained.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- Purchasing of Indirect require approval.

- The approval process should be applicable to the PO document type ZNPR and Purchasing organization.

- The approval matrix will be further reviewed during the Realize stage.

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Purchase Requisitions {#purchase-requisitions .LS_Heading-3}

  --------------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -------------------------------------
  NB                  Purchase Requisition   Used for indirect procurement items

  --------------------------------------------------------------------------------

## Purchase Orders {#purchase-orders .LS_Heading-3}

  --------------------------------------------------------------------------------
  **Document Type**   **Description**              **Comments**
  ------------------- ---------------------------- -------------------------------
  ZNPR                Purchase order for non-BOM   Purchase order for non-BOM

  --------------------------------------------------------------------------------

## Account Assignment Category [(TBD in Realize Stage)]{.mark} {#account-assignment-category-tbd-in-realize-stage .LS_Heading-3}

  ----------------------------------------------------------------------
  **Type**       **Description**         **Comments**
  -------------- ----------------------- -------------------------------
  K              Cost center             Cost center

  2              Cost center & Project   Cost center & Project

  P              Project                 Project
  ----------------------------------------------------------------------

##  Price Condition {#price-condition .LS_Heading-3}

  ----------------------------------------------------------------------------------------------------------------------
  **Type**       **Description**                    **Comments**
  -------------- ---------------------------------- --------------------------------------------------------------------
  ZTAX           Tax of indirect purchasing order   Need to set a default value of every indirect purchasing supplier.

  ----------------------------------------------------------------------------------------------------------------------

## Purchasing Organization of NPR in CN13&CN17 {#purchasing-organization-of-npr-in-cn13cn17 .LS_Heading-3}

  --------------------------------------------------------------------------------------------
  **Type**       **Description**                        **Comments**
  -------------- -------------------------------------- --------------------------------------
  R003           Home Control NPR Purchasing with TAX   Home Control NPR Purchasing with TAX

  --------------------------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Custom POs (ZNPR Doc Type) will be used for indirect purchases.

- Custom document number ranges will be used for Purchase orders [(TBD).]{.mark}

- PR/PO release strategies and workflows will be set up to support approvals as defined in section 2.6.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Expense postings can only be made in accounting periods open for posting.

- Postings in materials management can only be made in current and previous period. These must be in synch with open accounting periods.

- Requisitioner field will be mandatory.

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# Purchasing for Fixed Asset and Asset Under Construction {#purchasing-for-fixed-asset-and-asset-under-construction .LS_Heading-1}

3.  

<!-- -->

2.  

## Purpose {#purpose-1 .LS_Heading-3}

This scope item contains the creation and approval of purchase orders for fixed assets and Asset Under Construction. Alternatively, the process can also be triggered via a purchase requisition, which can then be converted to a purchase order. Subsequently, the invoice processes are triggered.

## Business Reason {#business-reason-1 .LS_Heading-3}

Purchasing for fixed assets and Asset Under Construction.

## Business Benefits {#business-benefits-1 .LS_Heading-3}

- Streamline procurement processes in an efficient and cost-effective manner.

- Ensure highly automated processes for the procurement of indirect.

- Reduce manual effort greatly.

- Monitor the procurement progress in real-time.

- Use an analytical list page to monitor purchase order items.

## Business Process for Fixed Asset and Asset Under Construction {#business-process-for-fixed-asset-and-asset-under-construction .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| **Step** | **Step Name**                               | **Role**        | **SAP App Name**                            | **Expected Results**                                                         |
+==========+=============================================+=================+=============================================+==============================================================================+
| 001      | request for Purchasing for Fix Asset or AUC | Requester       | Non-SAP                                     |                                                                              |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 002      | Fixed Asset or AUC?                         | Requester       | Non-SAP                                     |                                                                              |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 003      | Create project                              | Asset Finance   | Project Control - Enterprise Projects       | Create a project                                                             |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 004      | Create fixed asset                          | Asset Finance   | Manage fixed assets                         |                                                                              |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 005      | Create PR                                   | Requester       | My Purchase Requisitions - New              | Create service PR with Acct Assignment Category for fixed assets or project. |
|          |                                             |                 |                                             |                                                                              |
|          |                                             |                 |                                             | Need to choose the Acct Assignment Category of "3-way" or "2-way" match.     |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 006      | Change PR                                   | Requester       | My Inbox - All Items                        | Approve the PR                                                               |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 007      | PR approved?                                | Approver        | My Purchase Requisitions - New              | When PR is rejected, you can change PR to trigger re-approval.               |
|          |                                             |                 |                                             |                                                                              |
|          |                                             |                 |                                             | Xiaodong is an approver of the workflow to add attachment.                   |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 008      | Process PR to PO                            | Purchasing      | Process Purchase Requisitions (V2) (F1048A) | Process PR to PO                                                             |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 009      | PO approved?                                | Project Manager | My Inbox - All Items                        | Approve the PO                                                               |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 010      | Print PO                                    | Purchasing      | ME22N/Manage Purchase Orders                | Print PO if need.                                                            |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 011      | send PO to vendor                           | Purchasing      | ME22N/Manage Purchase Orders                | Send PO to vendor if need.                                                   |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 012      | Confirm Goods Receipt                       | Warehouse Admin | Non-SAP                                     |                                                                              |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 013      | If need to post goods receipt in SAP        | Requester       | Non-SAP                                     |                                                                              |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 014      | HC_SAP_DD_MM07_02_Post Goods Receipts       | Warehouse Admin | MIGO/Custom APP                             | Post goods receipts.                                                         |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+
| 015      | HC_SAP_DD_MM02_04_Invoice Verification      | AP admin        | /                                           | Invoice Verification                                                         |
+----------+---------------------------------------------+-----------------+---------------------------------------------+------------------------------------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements-1 .LS_Heading-3}

- Purchase Requisition created for indirect will require approval as defined by the D.O.A.

- Create service PR with Acct Assignment Category for fixed assets or project or others.

- Purchase Order created for indirect will require approval as defined by the D.O.A.

- PO output can be emailed to PO creator, using the email address maintained on the Workforce. The procurement team will download the PO manually and send it to the supplier or add a new output line to maintain supplier email in PO to send it to supplier.

- For indirect procurement under CN13/CN17, the purchase order (PO) shall include the tax-inclusive price, with the tax rate and tax condition type (ZTAX) set. After entering the price in the PO line item, the PO line item will display the tax-exclusive price, while the pricing conditions will show the tax-inclusive price, tax rate and tax-exclusive price.

- For indirect procurement under CN13/CN17, we need to use a purchasing organization.

- Some of the indirect purchases require 3-way match and some require 2-way match. It depends on Acct Assignment Category.

<!-- -->

- For fixed assets, the capitalization depends on invoice verification rather than goods receipt, and no FI documents are generated when fixed assets are posted goods receipts.

- PO output shall be emailed to Vendors and PO creator as PDF documents, no additional outputs (EDI, XML, Fax, etc.) shall be required.

- The system allows attachments to all documents in the procurement cycle:

  - PO's -- vendor quotes, signed contracts, etc.

<!-- -->

- SAP contract functionality is supported and will not be used in the current phase.

- Tax conditions -- Default tax code will be maintained.

- Do not need to post goods receipt for Purchasing of fixed assets.

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- Purchasing of Indirect require approval.

- The approval process should be applicable to the PO document type ZNPR and Purchasing organization.

- The approval matrix will be further reviewed during the Realize stage.

## Standard Documents / Settings  {#standard-documents-settings-1 .LS_Heading-3}

## Purchase Requisitions {#purchase-requisitions-1 .LS_Heading-3}

  --------------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -------------------------------------
  NB                  Purchase Requisition   Used for indirect procurement items

  --------------------------------------------------------------------------------

## Purchase Orders {#purchase-orders-1 .LS_Heading-3}

  --------------------------------------------------------------------------------
  **Document Type**   **Description**              **Comments**
  ------------------- ---------------------------- -------------------------------
  ZNPR                Purchase order for non-BOM   Purchase order for non-BOM

  --------------------------------------------------------------------------------

## Account Assignment Category[(TBD in Realize Stage)]{.mark} {#account-assignment-categorytbd-in-realize-stage .LS_Heading-3}

  ----------------------------------------------------------------------
  **Type**       **Description**         **Comments**
  -------------- ----------------------- -------------------------------
  A              Asset                   Asset-3-way

  2              Cost center & Project   Cost center & Project

  P              Project                 Project

                 Profit Center & Asset   Asset-2-way
  ----------------------------------------------------------------------

## Price Condition {#price-condition-1 .LS_Heading-3}

  ----------------------------------------------------------------------------------------------------------------------
  **Type**       **Description**                    **Comments**
  -------------- ---------------------------------- --------------------------------------------------------------------
  ZTAX           Tax of indirect purchasing order   Need to set a default value of every indirect purchasing supplier.

  ----------------------------------------------------------------------------------------------------------------------

## Purchasing Organization of NPR in CN13&CN17 {#purchasing-organization-of-npr-in-cn13cn17-1 .LS_Heading-3}

  --------------------------------------------------------------------------------------------
  **Type**       **Description**                        **Comments**
  -------------- -------------------------------------- --------------------------------------
  R003           Home Control NPR Purchasing with TAX   Home Control NPR Purchasing with TAX

  --------------------------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- Custom POs (ZNPR Doc Type) will be used for indirect purchases.

- Custom document number ranges will be used for Purchase orders [(TBD).]{.mark}

- PR/PO release strategies and workflows will be set up to support approvals as defined in section 3.6.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-1 .LS_Heading-3}

- Expense postings can only be made in accounting periods open for posting.

- Postings in materials management can only be made in current and previous period. These must be in synch with open accounting periods.

- Requisitioner field will be mandatory.

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

## Authorization Roles {#authorization-roles-1 .LS_Heading-3}

+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+
| **Business Role**               | **Role Description**                                                 | **Authorization Restrictions** | **Baseline ZRS Role(s)**                   |
+=================================+======================================================================+================================+============================================+
| Requester                       | - Create PRs                                                         | Std Roles                      | - Z\_ SAP_BR_EMPLOYEE_PROCUREMENT\_ Plant  |
|                                 |                                                                      |                                |                                            |
|                                 | - Change PRs                                                         | With some catalogs             |   (with catalog: SAP_MM_BC_SES_PROCESS_PC) |
|                                 |                                                                      |                                |                                            |
|                                 | - Create Service Entry Sheets                                        |                                |                                            |
+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+
| Approver                        | - Approve the PRs                                                    | Std Roles                      | - Z_SAP_BR_MANAGER_PROCUREMENT\_ Plant     |
+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+
| Purchasing/ Procurement         | - Manage POs (create, change, cancel, display) and Contracts         | Std Roles                      | - Z\_ SAP_BR_PURCHASER_Plant               |
|                                 |                                                                      |                                |                                            |
|                                 | - Monitor PO status                                                  |                                | - Z\_ SAP_BR_PROCUREMENT_Plant             |
|                                 |                                                                      |                                |                                            |
|                                 | - Process PO output on demand                                        |                                |                                            |
|                                 |                                                                      |                                |                                            |
|                                 | - Manage open PRs                                                    |                                |                                            |
+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+
| Purchasing manager /PO Approver | - Display and approve POs                                            | Std Roles                      | - Z_SAP_BR_PURCHASING_MANAGER_Plant        |
+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+
| Warehouse Admin                 | Role includes the following tasks related to procurement:            | Std Roles                      | Z_SAP_BR_WAREHOUSE_CLERK_Plant             |
|                                 |                                                                      |                                |                                            |
|                                 | - Posting goods receipts, returns                                    |                                |                                            |
|                                 |                                                                      |                                |                                            |
|                                 | - Document reversal in case of mistakes                              |                                |                                            |
|                                 |                                                                      |                                |                                            |
|                                 | - Initiate and process outbound deliveries in case of vendor returns |                                |                                            |
|                                 |                                                                      |                                |                                            |
|                                 | - PO search                                                          |                                |                                            |
|                                 |                                                                      |                                |                                            |
|                                 | - Inventory Display                                                  |                                |                                            |
+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+
| Purchasing Reporting            | - Purchasing analytics                                               | Std Roles Display access.      | - Z_SAP_BR_MASTER_DATA_VIEW_Plant          |
|                                 |                                                                      |                                |                                            |
|                                 | - All purchasing reports and list displays w/o create/update access  |                                |                                            |
+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+
| Accounts Payable Accountant     | - Enter vendor invoices, credit memos                                | Restricted by company code     | - Z\_ SAP_BR_AP_ACCOUNTANT_CompanyCode     |
|                                 |                                                                      |                                |                                            |
|                                 | - Process blocked invoices                                           |                                |                                            |
|                                 |                                                                      |                                |                                            |
|                                 | - Process vendor payments                                            |                                |                                            |
+---------------------------------+----------------------------------------------------------------------+--------------------------------+--------------------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  ----------------------------------------------------------------------------
  **Document Type**            **Document Flow**
  ---------------------------- -----------------------------------------------
  NB -- Standard requisition   MRP - NB requisition\
                               manual entry - NB requisition

  ZNPR                         Purchase order for non-BOM
  ----------------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

<!-- -->

6.  
7.  
8.  

<!-- -->

4.  
5.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| **SAP App**                        | **Description / Usage**                                                                                        |
+====================================+================================================================================================================+
| Procurement Overview               | KPI monitor and launchpad for crucial procurement task such as monitoring POs, PRs, spend, etc.                |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| My Purchase Requisitions New       | List and manage PRs of mine.                                                                                   |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| My Purchasing Documents Items      | Monitor and manage all documents related to purchasing -- PRs, POs, goods receipts, invoices                   |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Manage Purchase Orders             | List and manage POs                                                                                            |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Manage Purchase Requisitions       | List and manage PRs                                                                                            |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Monitor purchase requisition items | List and monitor status of open PRs                                                                            |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Monitor purchase order items       | List and monitor status of open POs                                                                            |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Procurement Analytics              | A collection of live expandable tiles with pre-configured KPI, including:                                      |
|                                    |                                                                                                                |
|                                    | - Overdue POs                                                                                                  |
|                                    |                                                                                                                |
|                                    | - Purchasing spend analysis                                                                                    |
|                                    |                                                                                                                |
|                                    | - Supplier evaluations (by quantity accuracy, by time accuracy, by price variances, by quality, overall score) |
|                                    |                                                                                                                |
|                                    | - Purchasing group (buyer) activity                                                                            |
|                                    |                                                                                                                |
|                                    | - Average PO delivery time                                                                                     |
|                                    |                                                                                                                |
|                                    | - PR approval time                                                                                             |
|                                    |                                                                                                                |
|                                    | - PR to PO cycle time                                                                                          |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+
| supplier invoice list              | - supplier invoice list                                                                                        |
+------------------------------------+----------------------------------------------------------------------------------------------------------------+

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

+---------------------------------------------------------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                                                                  |
+-----------------------------------------+-----------------------------------------+------------------+------------------+-------------------------+
| **Enhancement**                         | **Description**                         | **Complexity**   | **In Scope**     | **Comments**            |
+=========================================+=========================================+==================+==================+:========================+
| custom logic - send email to PO creator | custom logic - send email to PO creator | Small            | Yes              |                         |
+-----------------------------------------+-----------------------------------------+------------------+------------------+-------------------------+

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

+-------------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                                 |
+----------------------+-------------------+-------------------+-------------------+--------------------+
| **Workflow**         | **Description**   | **Complexity**    | **In Scope**      | **Comments**       |
+======================+===================+===================+===================+====================+
| PO Approval Workflow | Approvers are TBD | Med               | Yes               | For indirect order |
+----------------------+-------------------+-------------------+-------------------+--------------------+
| PR Approval Workflow | Approvers are TBD | Med               | Yes               | For indirect order |
+----------------------+-------------------+-------------------+-------------------+--------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image4.png){width="6.345306211723535in" height="2.3656714785651793in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
