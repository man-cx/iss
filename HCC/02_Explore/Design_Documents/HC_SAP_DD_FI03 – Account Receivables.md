**FICO Account Receivables**

**FICO应收账款**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: FI_DD_003 Account Receivables**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

       Frey Zheng               FICO Lead               08/06/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Jane Chen           Finance - Costing       

     Minting Wang              Finance            

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. J59 Account Receivables [5](#j59-account-receivables)](#j59-account-receivables)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [5](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[3. Process Scope Design [6](#process-scope-design)](#process-scope-design)

[3.1 Master dater [6](#master-dater)](#master-dater)

[3.1.1 Sales and Purchase Tax codes [6](#sales-and-purchase-tax-codes)](#sales-and-purchase-tax-codes)

[3.1.2 Reconciliation account [7](#reconciliation-account)](#reconciliation-account)

[3.1.3 Special GL Indicators [8](#special-gl-indicators)](#special-gl-indicators)

[3.1.4 Account determinations [8](#account-determinations)](#account-determinations)

[3.1.5 Payment Terms [9](#payment-terms)](#payment-terms)

[3.2 Manage Customer Incoming Payments [9](#manage-customer-incoming-payments)](#manage-customer-incoming-payments)

[3.2.1 Business Process Steps [9](#business-process-steps)](#business-process-steps)

[3.3 Manage Customer Down Payment [10](#manage-customer-down-payment)](#manage-customer-down-payment)

[3.3.1 Business Process Steps [10](#business-process-steps-1)](#business-process-steps-1)

[3.4 HC Functional Requirements [11](#hc-functional-requirements)](#hc-functional-requirements)

[3.5 HC Delegation Of Authority [11](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.6 Standard Documents / Settings [11](#standard-documents-settings)](#standard-documents-settings)

[3.7 Design Considerations / Key Assumptions [11](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.8 Cross Functional Integration Dependencies [11](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.9 Support / Closing Considerations [12](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [12](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [12](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [12](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [12](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [12](#reports)](#reports)

[6.1.1 Standard Reports [12](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [13](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [13](#interfaces)](#interfaces)

[6.3 Conversions [13](#conversions)](#conversions)

[6.4 Enhancements [14](#enhancements)](#enhancements)

[6.5 Forms [14](#forms)](#forms)

[6.6 Workflows [14](#workflows)](#workflows)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       08/06/2025

                                                              

                                                              
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

# J59 Account Receivables {#j59-account-receivables .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

With Accounts Receivable, you manage open receivables invoices that are automatically created from sales processes. Using various analytical tools, you can manage and control open items to optimize accounts receivables handling. The primary source of incoming payments is incoming bank statements that are loaded within the Cash Management process and automatically reconciled with open invoices. User-friendly views simplify and streamline the post processing of open items.

Alternatively, you can manually post incoming payments and easily reconcile the payment with an open item. Several analytical tools are available to monitor the receivables, allowing you to react quickly if you discover a declining payment discipline among your customers. You can effortlessly generate dunning letters for overdue items and track your customers\' dunning history.

## Business Reason {#business-reason .LS_Heading-3}

- Manage and complete customer master data

<!-- -->

- Analyze open items

- Reconcile open invoices with incoming payments automatically

- Process unassigned incoming payments to open invoices easily and efficiently

- Analyze efficiency of payment collection processing

- Process customer correspondence

## Business Benefits {#business-benefits .LS_Heading-3}

- Provide more detailed and comprehensive analysis of Accounts Receivable

- Provide automatic incoming payments clearing with the Electronic Bank Statement and rule-based reprocessing for incomplete items

- Process dunning of overdue items easily

- Process customer correspondence such as account statement or balance confirmation easily

# Process Scope Design {#process-scope-design .LS_Heading-1}

##  Master dater {#master-dater .LS_Heading-3}

## Sales and Purchase Tax codes {#sales-and-purchase-tax-codes .LS_Heading-3}

In order to determine and apply appropriate taxes on sales / purchase transactions, the sales tax codes and tax types need to be defined, configured and assigned to the Company code. Each tax code contains one or more tax rate for the different tax types. Further, these tax codes should be defined for the automatic posting and account determinations have to be carried out to enable automatic posting of taxes.

Followings are the system\'s predefined tax codes.

![](media/media/image2.emf)

Followings are the list of tax codes relevant for Singapore

  --------------------------------------------------------------------------------------------------
  **Tax code**   **Description**                      Tax rate      **G/L Account**    **Remarks**
  -------------- ------------------------------------ ------------- ----------------- --------------
  P0             Tax on purchases : zero percent      0%            1632000           

  P9             Tax on purchases 9%                  9%            1632000           

  [S2]{.mark}    [Tax on sales: Exempt]{.mark}        [0%]{.mark}   1631000           

  PS             Tax on purchases: Out of Scope: 0%   0%            1632000           

  S0             Tax on sales : zero percent          0%            1631000           

  S9             Tax on sales 9%                      9%            1631000           

  SN             Tax on sales (NO supplies) 0%        0%            1631000           

  SS             Tax on sales: Out of Scope: 0%       0%            1631000           
  --------------------------------------------------------------------------------------------------

Tax codes for China.

  ----------------------------------------------------------------------------------------------------------
  **Tax code**   **Description**                                Tax rate    **G/L Account**    **Remarks**
  -------------- ---------------------------------------------- ---------- ----------------- ---------------
  A1             CN 13% Tax on purchases: rebate for export 1   13%             1632000      

  A2             CN 3% Tax on purchases: rebate for export      3%              1632000      

  A3             CN 1% Tax on purchases: rebate for export      1%              1632000      

  J9             1632000                                        5%              1632000      

  JB             CN 5% Tax on purchases GL                      9%              1632000      

  JC             CN 1% Tax on purchases GL                      1%              1632000      

  X0             CN 0% Output Tax GL                            0%              1631000      

  X4             CN 0% Output Tax GL                            0%              1631000      

  X6             CN 9% Output Tax                               9%              1631000      

  J0             CN 0% Tax on purchases                         0%              1632000      

                                                                                             

  J2             CN 13% Tax on purchases                        13%             1632000      

                                                                                             

  J4             CN 6% Tax on purchases                         6%              1632000      

                                                                                             

  J6             CN 3% Tax on purchases                         3%              1632000      

                                                                                             

                                                                                             

  X2             CN 13% Output tax                              13%             1631000      

  X3             CN 6% Output tax                               6%              1631000      

  ZM             Tax on purchases: imports (0%)                 0%             1632000　     

  ZX             Tax on sales: exports (0%)                     0%             1631000　     
  ----------------------------------------------------------------------------------------------------------

Tax codes for Belgium

  ------------------------------------------------------------------------------------------------------------
  **Tax code**   **Description**                                  Tax rate   **G/L Account**     **Remarks**
  -------------- ------------------------------------------------ ---------- ----------------- ---------------
  00             Output VAT - 0% (not relevant for tax reports)   0%         1631000           

  A0             Output VAT - 0%                                  0%         1631000           

  A3             Output VAT - 21%                                 21%        1631000           

  A4             Output VAT - 0% (EU Tax Goods)                   0%         1631000           

  A5             Output VAT - 0% (EU Tax services)                0%         1631000           

  B3             VAT on bank charges 21%                          21%        1632000           

  D1             Input VAT - 21% - 50% non-deductible (al         21%        1632000           

  D2             Input VAT - 21% - 50% non-deductible (no         21%        1632000           

  E3             Acquisition VAT - 21% (goods)                    21%        1632000           

  F3             Acquisition VAT - 21% (subcontracting)           21%        1632000           

  G3             Acquisition VAT - 21% (50% non-ded/goods         21%        1632000           

  H3             Acquisition VAT - 21% (50% non-ded/goods         21%        1632000           

  V0             Input VAT - 0%                                   0%         1632000           

  V3             Input VAT - 21%                                  21%        1632000           
  ------------------------------------------------------------------------------------------------------------

## Reconciliation account  {#reconciliation-account .LS_Heading-3}

Invoice or other transaction data is posted to vendor/ customer via the sub-ledger account and the SAP system automatically posts the same data to General Ledger accounts. It is linked to the general ledger via the GL reconciliation account defined in the vendor/customer master. These reconciliation accounts ensure that the balance of the general ledger accounts is always the same as the sub-ledger. The postings within the AP/AR sub-ledger will affect the general ledger on the real-time basis. In this way, the General Ledger is always up to date and there is no need to transfer data from sub-ledger accounts to the General Ledger.

The reconciliation accounts for vendors/customer at HOME CONTROL are defined as follows:

  ------------------ ------------- --------------------------------------------------
   **Account Type**   **GL Code**                   **Description**

          D             1200000         Trade accounts rec.with domestic parties

          D             1200100         Trade accounts rec.with foreign parties

          K             1420000                    Advances to staff

          K             1427000                A/P Downpayments to Staff

          K             1430001                Advance payments to thirds

          D             1440000                  Other sundry acc.rec.

          K             1610000       Amounts owed to suppliers and trade credits

          K             1610005     Amts.owed to foreign suppliers and trade credits

          K             1610020              Accounts Payable to employees

          K             1632600      Other taxes-Customs office-Import VAT payable

          K             1632610             Other taxes-Customs office-Duty

          K             1691000     Other accounts payable non-int.bearing-pers.rel.

          D             5100000           Philips ICA receivable-invoice sent

          D             5100002       Philips ICA foreign receivable-invoice sent

          D             5100020                Philips current A/R Local

          K             5110000             Philips ICA payable-invoice sent

          K             5110002         Philips ICA foreign payable-invoice sent

          K             5120102                     ISA ICA Payable

          K             5140000                  Philips ICA dividends

          K             5190000              Philips ICA restricted shares

          D             5430110             Loans to cons.comp.- short term

          D             5500100           Interdepartmental a/c NO Receivable

          K             5500200             Interdepartmental a/c NO Payable

          D             1200000         Trade accounts rec.with domestic parties
  ------------------ ------------- --------------------------------------------------

## Special GL Indicators {#special-gl-indicators .LS_Heading-3}

Special GL indicators are defined when certain transactions reflected in a sub-ledger needs to be reflected in an alternate reconciliation account (different from the reconciliation account for the respective sub-ledger). For example, Advances paid to vendors are reflected in the vendors account in sub-ledger (as a special GL transaction) whereas in the General ledger, the advance would appear under 'Advances to Vendors'(alternative reconciliation account) for which a special GL indicator needs to be configured. Similarly, if statistical postings like advance payment request, letters of credits should be reflected in the general ledger, a special GL indicator needs to be configured.

In SAP cloud ERP, the special general ledger indicators cannot be customized added. The standard default special general ledger indicators provided by the system is as follows.

The special general ledger indicators required by HC can only be selected from the values provided by SAP.

![](media/media/image3.emf)

## Account determinations {#account-determinations .LS_Heading-3}

While configuring certain automatic postings in the SAP system, the GL account numbers (created in chart of accounts YCOA) relevant to HOME CONTROL should be defined. Examples of such automatic posting are sales tax and excise postings, exchange rate differences, cash discount and bank charges, offsetting entries in special GL transactions, etc.

## Payment Terms {#payment-terms .LS_Heading-3}

In order for the system to determine and apply the terms of payment for purchase and sales transactions, the rules are defined and stored under a four-character key. Then, the key is assigned to the vendor / customer through the respective master record.

The baseline date is calculated based on the document date.

The same key for the terms of payment can be used for both customers and vendors who have the same payment terms

[Please update the latest data.]{.mark}

![](media/media/image4.emf)

## Manage Customer Incoming Payments {#manage-customer-incoming-payments .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+------------------------------------------------------------------------------------------------+-----------------------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| Process Step                                                                                   | Business Role         | Transaction/App           | Expected Results                                                                                                            |
+================================================================================================+=======================+===========================+=============================================================================================================================+
| 1.  Collection -Receive payment from customer                                                  | AR processing officer | N/A                       | N/A                                                                                                                         |
+------------------------------------------------------------------------------------------------+-----------------------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| 2.  AR processing officer verifies the collection amount against the list of customer invoices | AR processing officer | Customer Line Items China | View all line items of a certain customer account and all outstanding customer invoices that are overdue as of the key date |
+------------------------------------------------------------------------------------------------+-----------------------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------+
| 3.  Process incoming payment and AR Account Clearing                                           | AR processing officer | Post Incoming Payments    | Incoming payment is posted, and customer invoice is cleared                                                                 |
+------------------------------------------------------------------------------------------------+-----------------------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------+

1.  

    1.  

## Manage Customer Down Payment {#manage-customer-down-payment .LS_Heading-3}

![](media/media/image6.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| Process Step                                                                               | Business Role         | Transaction/App                                                | Expected Results                                   |
+============================================================================================+=======================+================================================================+====================================================+
| 1.  Planner creates Performance Invoice                                                    | Planner               | Create Billing Documents，Billing Type：F5 Pro Forma for Order | N/A                                                |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| 2.  The invoice is sent to customer                                                        | Planner               | N/A                                                            | N/A                                                |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| 3.  Planner submits Down Payment Request on SAP                                            | Planner               | Manage Customer Down Payment Requests                          | Customer Down Payment Request is created           |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| 4.  Finance receives Bank Statement                                                        | AR Processing Officer | N/A                                                            | N/A                                                |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| 5.  Finance manually confirms with Planner on the reference number of Down Payment request | AR Processing Officer | N/A                                                            | N/A                                                |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| 6.  Finance makes relevant posting for Down Payment Made                                   | AR Processing Officer | Post Incoming Payments                                         | Incoming Payments is posted                        |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| 7.  Finance informs Planner that Down Payment posting has been made                        | AR Processing Officer | N/A                                                            | N/A                                                |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+
| 8.  Down Payment Clearing                                                                  | AR Processing Officer | Clear Incoming Payments Manual Clearing                        | Incoming Payments and customer invoice are cleared |
+--------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------+----------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- Manage Customer Incoming Payments:

> Ability to generate aging reports by customer and standard period segments of outstanding balances (e.g. 1-30 days, 31-60 etc), as well as ability to sort ageing report by customers

- Manage Customer Down Payment:

> System provides the Down payment notes and down payment clearing functionalities

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- Customer Down Payment Request do not require approval in SAP system.

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- The basic functionality of Incoming payments is to record such payments and at the same time clear customer open items which can be full or partial. Alternatively, residual postings can also be generated.

- SAP cloud ERP uses partial clearing by default, and the function of residual clearing can be realized by displaying the remaining amount field.

- Customer down payment requests is noted items i.e. one line posting is done without having any financial impact.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- With Sales and Distribution (SD): Receives sales orders and invoice data, serves as the source of accounts receivable, and synchronizes customer transaction information.

- With Financial Accounting (FI): Real-time posting of accounts receivable balances to corresponding general ledger accounts, affecting financial statement data.

- cash management: Synchronizes collection records to the cash module, completes accounts receivable clearing, and updates cash flow.

- Customer Master Data: Shares basic customer information (such as credit limits, payment terms, etc.) to support credit control.

- Credit Management: Dynamically adjusts credit limits and controls the risk of bad debts based on accounts receivable balances and payment records.

- With Materials Management (MM): Links with shipment and delivery information to ensure that invoices match the goods flow and avoid abnormal accounts receivable.

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

+-----------------------+------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| **Business Role**     | **Role Description**                                                                           | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+=======================+================================================================================================+================================+==========================+
| AR processing officer | Role includes the following key system tasks:                                                  | Std Roles                      | - BR_AR_ACCOUNTANT       |
|                       |                                                                                                |                                |                          |
|                       | - Responsible to receive, execute collection document and clear customer invoices              |                                |                          |
+-----------------------+------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| AR processing officer | - Responsible to process down payment request and clear the down payment with customer invoice | Std Roles                      | - BR_AR_ACCOUNTANT       |
+-----------------------+------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+

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

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **SAP App**                                **Description / Usage**
  ------------------------------------------ -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Display Cusomer Summary China              It is used to summarize the information of customer-related inter-account items. It can perform classified summary by customer or account, display the collection amount and receivable amount of each customer or general ledger account within a specified period, and also show the opening and closing balances of each selected period, with support for drilling down to detailed customer reports.

  Customer Line Items China                  Easily find customer line items using a variety of search criteria, and display all open or cleared details.

  Aging Report - Accounts Receivable China   It is mainly used to show the aging distribution of accounts receivable, helping enterprises understand the duration of customers\' arrears for risk assessment and collection management.

                                             
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                                                                                                              |
+------------------------------------+-------------------------------------------------------------------+----------------+------------------------------------------+----------------+--------------------+
| **Report Name**                    | **Description**                                                   | **Key Files**  | **Std.**                                 | **Complexity** | **Comment**        |
|                                    |                                                                   |                |                                          |                |                    |
|                                    |                                                                   |                | **SAP App/Rprt**                         |                |                    |
+:===================================+===================================================================+:===============+:=========================================+:===============+:===================+
| Aging Report - Accounts Receivable | The aging analysis report for AR needs to be displayed in detail. |                | Aging Report - Accounts Receivable China | Small          |                    |
+------------------------------------+-------------------------------------------------------------------+----------------+------------------------------------------+----------------+--------------------+

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

+---------------------------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                                             |
+-------------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**                      | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|                               |                   |                           |                            | (# items)**   |                |
+===============================+===================+===========================+============================+===============+================+
| Accounts Receivable open item | ECC               | Low                       | Med                        | TBD           |                |
|                               |                   |                           |                            |               |                |
| 应付账款未清项                |                   |                           |                            |               |                |
+-------------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|                               |                   |                           |                            |               |                |
+-------------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+

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

+---------------------------------------------------------------------------------------------------+
| **Forms**                                                                                         |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Form**          | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **表单​​**          | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

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
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **​​灵活工作流​​**    | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
