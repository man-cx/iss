**FICO Account Payable**

**FICO应付账款**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: FI_DD_002 Account Payable**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

       Frey Zheng               FICO Lead               08/05/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Jane Chen              Finance - GL         

     Minting Wang              Finance            

      Sally Jin           Finance - Bank/GL       

      Nicole Li              Finance - AP         

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. J60 Accounts Payable [5](#j60-accounts-payable)](#j60-accounts-payable)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [5](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[3. Process Scope Design [6](#process-scope-design)](#process-scope-design)

[3.1 Master dater [6](#master-dater)](#master-dater)

[3.1.1 House Banks [6](#house-banks)](#house-banks)

[3.1.2 Payment Method [6](#payment-method)](#payment-method)

[3.1.3 Terms of Payment [7](#_Toc205395019)](#_Toc205395019)

[3.2 Manage Invoice Processing without PO [8](#manage-invoice-processing-without-po)](#manage-invoice-processing-without-po)

[3.2.1 Business Process Steps [8](#business-process-steps)](#business-process-steps)

[3.3 Business Process for Manage GL Master Records [9](#business-process-for-manage-gl-master-records)](#business-process-for-manage-gl-master-records)

[3.3.1 Business Process Steps [9](#business-process-steps-1)](#business-process-steps-1)

[3.4 Manage Vendor Down Payment [10](#manage-vendor-down-payment)](#manage-vendor-down-payment)

[3.4.1 Business Process Steps [10](#business-process-steps-2)](#business-process-steps-2)

[3.5 HC Functional Requirements [11](#hc-functional-requirements)](#hc-functional-requirements)

[3.6 HC Delegation Of Authority [11](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.7 Standard Documents / Settings [11](#standard-documents-settings)](#standard-documents-settings)

[3.7.1 Payment proposal [11](#payment-proposal)](#payment-proposal)

[3.7.2 Supplier Down Payment Request [11](#supplier-down-payment-request)](#supplier-down-payment-request)

[3.8 Design Considerations / Key Assumptions [12](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.9 Cross Functional Integration Dependencies [12](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.10 Support / Closing Considerations [12](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [12](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [12](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [13](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [13](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [13](#reports)](#reports)

[6.1.1 Standard Reports [13](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [14](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [14](#interfaces)](#interfaces)

[6.3 Conversions [14](#conversions)](#conversions)

[6.4 Enhancements [15](#enhancements)](#enhancements)

[6.5 Forms [15](#forms)](#forms)

[6.6 Workflows [15](#workflows)](#workflows)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       08/05/2025

                                                              

                                                              
  ------------- --------------------------------------------- --------------------

# Guidelines {#guidelines .LS_Heading-1}

## Design Document Approval Overview {#design-document-approval-overview .LS_Heading-3}

The SAP Implementation Project Design Documents are the result of the Fit / Gap workshops.  All Project Design Documents must be reviewed and approved by the Home Control team to confirm we have captured the appropriate requirements as well as gaps, proposed solutions, and RICEFW objects​ from the workshops.

SAP Design Documents are living, breathing documents. As the SAP system is configured, tested, modified, and approved, the design documents may be updated to reflect the final design​.

Answerthink Team Leads create the original design documents​. Should Home Control decide to update the Design Documents, it is up to Home Control to perform the updates.

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

# J60 Accounts Payable {#j60-accounts-payable .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

With Accounts Payable, you manage your open payable invoices that are automatically created from purchasing processes.

You manage and control open items with various analytical tools. You plan future payables and analyze the outcome of payments, such as utilization of cash discounts and days payables outstanding.

Automate processing of your outstanding payables and monitor payment progress.

you can also download generated payment files to streamline the connectivity to the banks for payments and bank statements.

## Business Reason {#business-reason .LS_Heading-3}

- Manage and complete supplier master data

- Create invoice from logistics

- Analyze outstanding payables

- Pay invoices

- Approve payments (optional)

- Download payment file

<!-- -->

- Analyze efficiency of payment processing

## Business Benefits {#business-benefits .LS_Heading-3}

- Integrate accounts payable into procurement

- Record accounts payable posting directly in the general ledger

- Use payment program to automatically create instructions for bank transfers

- Use payment approval for workflow

- Download the payment instruction file for further manual processing

- Analyze the efficiency of your payment processing

# Process Scope Design {#process-scope-design .LS_Heading-1}

##  Master dater {#master-dater .LS_Heading-3}

## House Banks {#house-banks .LS_Heading-3}

The banks with which HOME CONTROL maintains a bank account are referred to as house banks.

Every bank account will be configured as house bank & account id in SAP. Bank main account will be assigned to each of the house banks.

Bank master data (Bank Key) will be stored centrally in the SAP system. This includes address data and other control data, such as the SWIFT code. Bank Key will be assigned to house bank.

Following is the sample list of house banks configured for HOME CONTROL. Full list of house bank will be available in configuration document.

[Please update the latest data.]{.mark}

[List of house banks-update.xlsx](https://omnidevices-my.sharepoint.com/personal/sally_jin_omnidevices_com/_layouts/15/Doc.aspx?sourcedoc=%7BB566303A-BD9E-4E74-BB41-0846457A96B3%7D&file=List%20of%20house%20banks-update.xlsx&action=default&mobileredirect=true)

## Payment Method {#payment-method .LS_Heading-3}

For each separate mode of payment to the vendor/customer, a payment method will be set up in the SAP system.

Payment method can be entered in the vendor/customer master data so that the invoices processed can inherit the payment method from the vendor master.

If different payment method is required for a particular invoice, the payment method can be specified during invoice entry.

Based on the payment method entered in the vendor/customer master or the invoice entry, the payment program will select the correct payment method to use during periodic payment processing.

[Please update the latest data.]{.mark}

Following is the list of payment method

  -------------------------- -------------------- ----------------------------- ----------------
         **Co. Code**         **Payment Method**         **Description**          **Remarks**

        SG21/CN13/CN17                1              Internal bank transfer     

        SG21/CN13/CN17                D                 Domestic Payment         Bank-interface

        SG21/CN13/CN17                I            International Bank transfer   Bank-interface

   SG21/CN13/CN17/BE10/US10           M                  Manual Payment         
  -------------------------- -------------------- ----------------------------- ----------------

## Manage Invoice Processing without PO {#manage-invoice-processing-without-po .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+-------------------------------------------------------------------------------------------------------+-----------------------+--------------------------+------------------------------+
| Process Step                                                                                          | Business Role         | Transaction/App          | Expected Results             |
+=======================================================================================================+=======================+==========================+==============================+
| 1.  Receipt of invoice from Vendors for non-PO/SO                                                     | N/A                   | N/A                      | N/A                          |
+-------------------------------------------------------------------------------------------------------+-----------------------+--------------------------+------------------------------+
| 2.  Finance and/or end user signs on original invoices                                                | N/A                   | N/A                      | N/A                          |
+-------------------------------------------------------------------------------------------------------+-----------------------+--------------------------+------------------------------+
| 3.  Physical Verification of Invoices by Finance. Hard copy documents have been approved by BU's HOD. | AP processing officer | N/A                      | N/A                          |
+-------------------------------------------------------------------------------------------------------+-----------------------+--------------------------+------------------------------+
| 4.  (Only applicable to Singapore) The invoices will be sent to Account Payable team in China         | AP processing officer | N/A                      | N/A                          |
+-------------------------------------------------------------------------------------------------------+-----------------------+--------------------------+------------------------------+
| 5.  Finance Authorizer posts invoice without Purchase Order / Service Order in the system             | AP processing officer | Create Incoming Invoices | Supplier invoice is created. |
+-------------------------------------------------------------------------------------------------------+-----------------------+--------------------------+------------------------------+

1.  

    1.  

## Business Process for  Manage GL Master Records {#business-process-for-manage-gl-master-records .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| Process Step                                                                                                                                               | Business Role         | Transaction/App                    | Expected Results                                                                                                        |
+============================================================================================================================================================+=======================+====================================+=========================================================================================================================+
| 1.  AP officer checks invoices which have been approved and pending for payment                                                                            | AP processing officer | Supplier Line Items China          | View all line items of a certain vendor account and all outstanding vendor invoices that are overdue as of the due date |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| 2.  AP officer generates proposal                                                                                                                          | AP processing officer | Process Payment Items for Invoices | Payment proposal is generated                                                                                           |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| 3.  AP officer reviews and edits Proposal List & Exception List. Investigated/Exception rectified.                                                         | AP processing officer | Process Payment Items for Invoices | Payment proposal is revised                                                                                             |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| 4.  AP officer sends email to manager for approval                                                                                                         | AP processing officer | N/A                                | N/A                                                                                                                     |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| 5.  Certain payments will be blocked                                                                                                                       | AP processing officer | Process Payment Items for Invoices | Payment proposal is blocked                                                                                             |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| 6.  AP officer executes payment run and prints payment report                                                                                              | AP processing officer | Process Payment Items for Invoices | Payment run and payment report is printed                                                                               |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| 7.  Manual payment will be executed for urgent PO and non-PO invoices following by AP Clearing. Payment is made via CitiDirect or HSBC Net Payment Program | AP processing officer | Post Outgoing Payments             | Outgoing payment is posted, and supplier invoice is cleared                                                             |
+------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

## Manage Vendor Down Payment {#manage-vendor-down-payment .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

+------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------+----------------------------------------------+
| Process Step                                                                                                                                         | Business Role         | Transaction/App                       | Expected Results                             |
+======================================================================================================================================================+=======================+=======================================+==============================================+
| 1.  Requestor creates Down Payment Request from PO and submits the request form to Department manager for approval                                   | Requestor             | Manage Supplier Down Payment Request  | Supplier Down Payment Request is created     |
+------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------+----------------------------------------------+
| 2.  Department Manager reviews down payment request, If approved, connect to the outgoing payment process; if not approved, notified the requestor   | Department Manager    | Verify Supplier Down Payment Requests | Down payment request is approved or rejected |
|                                                                                                                                                      |                       |                                       |                                              |
|                                                                                                                                                      |                       | Approver Inbox                        |                                              |
+------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------+----------------------------------------------+
| 3.  Finance reviews down payment request, If approved, it is submitted to the finance department for review; if not approved, notified the requestor | AP processing officer | Verify Supplier Down Payment Requests | Down payment request is approved or rejected |
|                                                                                                                                                      |                       |                                       |                                              |
|                                                                                                                                                      |                       | Approver Inbox                        |                                              |
+------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+---------------------------------------+----------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- Manage Invoice Processing without PO:

> Invoice posting without PO can be done either through invoice verification or direct FI AP posting. The generated AP Accounting Documents number should be in sequence with other AP Accounting documents

- Manage Vendor Outgoing Payments

> Bank interfaces are required to transfer the payment information from SAP to the bank electronically

- Manage Vendor Down Payment

> Down payment request is needed in system for noting down the payment request, which can also be included in the auto-payment proposal

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- Payment proposals do not require approval in SAP system.

- The approval process should be applicable to the Supplier Down payment Request

- The approval matrix will be further reviewed during the Realize stage

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Payment proposal {#payment-proposal .LS_Heading-3}

  -----------------------------------------------------------------------------------------------------------------------
  **Document Type**   **Description**    **Comments**
  ------------------- ------------------ --------------------------------------------------------------------------------
                      Payment proposal   Payment proposals automatically generated by the system based on open invoices

  **​​文档类型​​**        **​​描述​​**           **​​注释​​**

  ​**​**                付款建议           系统根据未清发票自动生成的付款建议
  -----------------------------------------------------------------------------------------------------------------------

## Supplier Down Payment Request {#supplier-down-payment-request .LS_Heading-3}

  --------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -------------------------------
                      Down payment Request   Down payment Request

  **​​文档类型​​**        **​​描述​​**               **​​注释​​**

  ​**​**                供应商预付款请求       供应商预付款请求
  --------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Payment Run enables clearing of Open items in vendor account and corresponding Accounting Document will be generated automatically through system.

<!-- -->

- Config the approval workflow for supplier down payment requests within the system

- Supplier down payment requests is noted items i.e. one line posting is done without having any financial impact.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- With Materials Management (MM): Achieving three-way matching through purchase orders, goods receipts, and invoices, and synchronizing vendor and material master data.

- With Financial Accounting (FI): Automatically generating general ledger vouchers, linking asset accounting and bank accounting to ensure consistent financial data.

- With Sales and Distribution (SD): Supporting combined reconciliation of customers and vendors, and processing rebates based on sales data.

- With Controlling (CO): Linking cost centers and profit centers to realize cost accumulation and analysis.

- With external systems: Capable of connecting to external electronic invoice platforms via EDI (Electronic Data Interchange) or APIs; integrable with bank payment gateways and third-party payment tools. Payment instructions from the AP module directly trigger payment operations in external systems and synchronously return payment results.

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

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

+-----------------------+-----------------------------------------------+--------------------------------+--------------------------+
| **Business Role**     | **Role Description**                          | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+=======================+===============================================+================================+==========================+
| Requestor             | Role includes the following key system tasks: | Std Roles                      | - BR_AP_ACCOUNTANT       |
|                       |                                               |                                |                          |
|                       | - Create the Vendor Down Payment Request      |                                |                          |
+-----------------------+-----------------------------------------------+--------------------------------+--------------------------+
| Department Manager    | - Approve Vendor Down Payment Request         | Std Roles                      | - BR_AP_ACCOUNTANT       |
+-----------------------+-----------------------------------------------+--------------------------------+--------------------------+
| AP processing officer | - Responsible to post invoice (without PO)    | Std Roles                      | - BR_AP_ACCOUNTANT       |
|                       |                                               |                                |                          |
|                       | - Responsible to execute the vendor payment   |                                |                          |
|                       |                                               |                                |                          |
|                       | - Approve Vendor Down Payment Request         |                                |                          |
+-----------------------+-----------------------------------------------+--------------------------------+--------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------
  N/A                     

                          

                          

                          

                          
  -----------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **SAP App**                             **Description / Usage**
  --------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Display Supplier Summary China          Query supplier payables and details including opening balance, current period increases, current period decreases, and remaining balance by different dimensions, presenting the arrears of individual or overall suppliers.

  Supplier Line Items China               View all line items of a specific supplier account and all outstanding supplier invoices that are overdue as of the key date.

  Aging Report - Accounts Payable China   List outstanding payables by key date and time intervals, with support for setting multiple aging periods, flexible sorting, and currency selection, facilitating the analysis of overdue situations and fund arrangement.
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                                                                                                         |
+---------------------------------+-------------------------------------------------------------------+----------------+---------------------------------------+----------------+---------------------+
| **Report Name**                 | **Description**                                                   | **Key Files**  | **Std.**                              | **Complexity** | **Comment**         |
|                                 |                                                                   |                |                                       |                |                     |
|                                 |                                                                   |                | **SAP App/Rprt**                      |                |                     |
+:================================+===================================================================+:===============+:======================================+:===============+:====================+
| Aging Report - Accounts Payable | The aging analysis report for AP needs to be displayed in detail. |                | Aging Report - Accounts Payable China | Small          |                     |
+---------------------------------+-------------------------------------------------------------------+----------------+---------------------------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                 |
+------------------+------------------+------------------+------------------+--------------------+
| **Interface**    | **Description**  | **In Scope**     | **Complexity**   | **Comments**       |
+:=================+:=================+:=================+:=================+:===================+
| N/A              |                  |                  |                  |                    |
+------------------+------------------+------------------+------------------+--------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

范围内需要切换的数据如下

+------------------------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                                          |
+----------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**                   | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|                            |                   |                           |                            | (# items)**   |                |
+============================+===================+===========================+============================+===============+================+
| Accounts payable open item | ECC               | Low                       | Med                        | TBD           |                |
|                            |                   |                           |                            |               |                |
| 应付账款未清项             |                   |                           |                            |               |                |
+----------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|                            |                   |                           |                            |               |                |
+----------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+-----------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                    |
+------------------+------------------+------------------+------------------+-------------------------+
| **Enhancement**  | **Description**  | **Complexity**   | **In Scope**     | **Comments**            |
+==================+==================+==================+==================+:========================+
| N/A              |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+
|                  |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+
|                  |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+

## Forms {#forms .LS_Heading-3}

The following forms have been identified as in scope:

+--------------------------------------------------------------------------------------------------------------+
| **Forms**                                                                                                    |
+-------------------+------------------------------+-------------------+-------------------+-------------------+
| **Form**          | **Description**              | **Complexity**    | **In Scope**      | **Comments**      |
+===================+==============================+===================+===================+===================+
| Payment proposal  | Payment proposal output form | Med               | Yes               |                   |
+-------------------+------------------------------+-------------------+-------------------+-------------------+
|                   |                              |                   |                   |                   |
+-------------------+------------------------------+-------------------+-------------------+-------------------+
| **表单​​**          | **​​描述​​**                     | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+------------------------------+-------------------+-------------------+-------------------+
| 付款建议          | 付款建议输出表单             | 中等              | 是                |                   |
+-------------------+------------------------------+-------------------+-------------------+-------------------+
|                   |                              |                   |                   |                   |
+-------------------+------------------------------+-------------------+-------------------+-------------------+

## Workflows {#workflows .LS_Heading-3}

The following workflows have been identified as in scope:

以下工作流被纳入范围：

+---------------------------------------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                                                           |
+-------------------------------------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**                                    | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+=================================================+===================+===================+===================+===================+
| Supplier Down Payment Request Approval Workflow | Std Workflow      | Med               | Yes               |                   |
+-------------------------------------------------+-------------------+-------------------+-------------------+-------------------+
|                                                 |                   |                   |                   |                   |
+-------------------------------------------------+-------------------+-------------------+-------------------+-------------------+
| **​​灵活工作流​​**                                  | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------------------------------------+-------------------+-------------------+-------------------+-------------------+
| 供应商预付款申请审批                            | 标准工作流        | 中等              | 是                |                   |
+-------------------------------------------------+-------------------+-------------------+-------------------+-------------------+
|                                                 |                   |                   |                   |                   |
+-------------------------------------------------+-------------------+-------------------+-------------------+-------------------+

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
