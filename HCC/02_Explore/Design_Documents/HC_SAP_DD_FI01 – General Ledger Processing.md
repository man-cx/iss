**FICO General Ledger Processing**

**FICO总账流程**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: FI_DD_001 General Ledger Processing**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

       Frey Zheng               FICO Lead               08/05/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

     Jianwei Shi               Finance            

     Minting Wang              Finance            

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [5](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [5](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. J58 Accounting and Financial Close [6](#j58-accounting-and-financial-close)](#j58-accounting-and-financial-close)

[2.1 Purpose [6](#purpose)](#purpose)

[2.2 Business Reason [6](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[3. Process Scope Design [7](#process-scope-design)](#process-scope-design)

[3.1 Organizational Structure and Master dater [7](#organizational-structure-and-master-dater)](#organizational-structure-and-master-dater)

[3.1.1 Flow Chart -- Organizational Structure [7](#flow-chart-organizational-structure)](#flow-chart-organizational-structure)

[3.1.2 Company Code [7](#company-code)](#company-code)

[3.1.3 Functional Area [7](#functional-area)](#functional-area)

[3.1.4 Chart of Accounts [8](#chart-of-accounts)](#chart-of-accounts)

[3.1.5 Parallel ledger [8](#parallel-ledger)](#parallel-ledger)

[3.1.6 Account Group (GL Account) [9](#account-group-gl-account)](#account-group-gl-account)

[3.1.7 Fiscal Year Variant [10](#fiscal-year-variant)](#fiscal-year-variant)

[3.1.8 Exchange Rate Type [10](#exchange-rate-type)](#exchange-rate-type)

[3.1.9 Document Type [10](#document-type)](#document-type)

[3.1.10 Bank Keys [10](#bank-keys)](#bank-keys)

[3.1.11 Trading partner [11](#trading-partner)](#trading-partner)

[3.2 Business Process for Manage GL Master Records [12](#business-process-for-manage-gl-master-records)](#business-process-for-manage-gl-master-records)

[3.2.1 Business Process Steps [12](#business-process-steps)](#business-process-steps)

[3.3 Manage Posting in GL and Parallel Ledger [14](#manage-posting-in-gl-and-parallel-ledger)](#manage-posting-in-gl-and-parallel-ledger)

[3.3.1 Business Process Steps [14](#business-process-steps-1)](#business-process-steps-1)

[3.4 Bank Master Data [15](#bank-master-data)](#bank-master-data)

[3.4.1 Business Process Steps [15](#business-process-steps-2)](#business-process-steps-2)

[3.5 Month End Closing Operations [16](#month-end-closing-operations)](#month-end-closing-operations)

[3.5.1 Business Process Steps [16](#business-process-steps-3)](#business-process-steps-3)

[3.6 Manage Balance Carryforward [18](#manage-balance-carryforward)](#manage-balance-carryforward)

[3.6.1 Business Process Steps [18](#business-process-steps-4)](#business-process-steps-4)

[3.7 HC Functional Requirements [18](#hc-functional-requirements)](#hc-functional-requirements)

[3.8 HC Delegation Of Authority [19](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.9 Standard Documents / Settings [19](#standard-documents-settings)](#standard-documents-settings)

[3.9.1 Journal Entries list [19](#journal-entries-list)](#journal-entries-list)

[3.9.2 Journal Entries [19](#journal-entries)](#journal-entries)

[3.10 Design Considerations / Key Assumptions [19](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.11 Cross Functional Integration Dependencies [19](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.12 Support / Closing Considerations [20](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [20](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [20](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [21](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [21](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [21](#reports)](#reports)

[6.1.1 Standard Reports [21](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [22](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [22](#interfaces)](#interfaces)

[6.3 Conversions [23](#conversions)](#conversions)

[6.4 Enhancements [23](#enhancements)](#enhancements)

[6.5 Forms [23](#forms)](#forms)

[6.6 Workflows [24](#workflows)](#workflows)

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

# J58 Accounting and Financial Close {#j58-accounting-and-financial-close .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

The SAP organizational structure defines the backbone of the SAP system and is linked to every transaction and master data element in the SAP system. The SAP Organizational Structure becomes the means to deliver:

- Management information

- Business segmentation

- Geographic structure alignments

- Reporting requirements

In general, the SAP organization structure is the fundamental data and functional architecture within the SAP system and is comprised of several customizable organizational entities. The organization structure is central to the operation of the software and is a prerequisite to configuration. The organizational structure encourages common business processes, master data standards, and is usually difficult to change once established.

the purpose of scenarios related to SAP FI master data is to create, maintain, and manage various types of financial master data, ensuring that such master data can support the recording, processing, accounting of financial transactions and meet reporting requirements, serving as the basic data support for the smooth operation of financial processes.

## Business Reason {#business-reason .LS_Heading-3}

The organizational structure is a digital abstraction of an enterprise\'s real business entities (such as companies, departments, factories, etc.), ensuring that the system can accurately reflect the enterprise\'s management model and operational logic.

These financial master data are the core foundation for carrying out various financial and related business processes. Without these master data, financial transactions cannot be accurately posted and accounted for, financial statements cannot be prepared normally, business processes cannot proceed smoothly, and various reporting and management needs of the business cannot be met.

## Business Benefits {#business-benefits .LS_Heading-3}

The organizational structure of SAP serves as a \"bridge\" connecting an enterprise\'s actual business operations with system functions. Its core significance lies in:

- Defining the enterprise\'s business boundaries, responsibility relationships, and data dimensions in a digital manner.

- It not only ensures the standardization and efficiency of business processes but also supports the integration and analysis of data, while possessing the flexibility to adapt to the enterprise\'s development.

Through the effective management of these financial master data, standardized and consistent recording and processing of financial data can be achieved, reducing data errors and redundancies; it supports the automation and efficient operation of various financial processes, improving the efficiency of financial work; it provides an accurate and reliable data foundation for financial statement preparation, business analysis, management decision-making, etc., meets compliance requirements, and at the same time helps enterprises better conduct cost control, risk management and business optimization.

- Record all business transactions to ensure complete and accurate accounting data

# Process Scope Design {#process-scope-design .LS_Heading-1}

##  Organizational Structure and Master dater {#organizational-structure-and-master-dater .LS_Heading-3}

## Flow Chart -- Organizational Structure {#flow-chart-organizational-structure .LS_Heading-3}

The below flow Chart depicts the Finance and Controlling High Level Organization structure

![](media/media/image2.emf)

## Company Code {#company-code .LS_Heading-3}

Generally considered the smallest organizational unit to meet external accounting needs for which a complete, self-contained set of accounts can be created. This includes the entry of all transactions that must be posted and the creation of all items for legal individual financial statements, such as the balance sheet and the profit and loss statement.

  ------------------------------------------------------------
  **Company Code**   **Company Name**
  ------------------ -----------------------------------------
  SG21               Home Control Singapore Pte Ltd 

  CN13               HC (Suzhou) Limited 

  CN17               Home Control Solutions (Suzhou) Limited

  US10               Premium Home Control Solutions LLC 

  BE10               Home Control Europe NV 

  HCIL               Home Control International Limited

  BR10               Omni Remotes Do Brasil Ltda
  ------------------------------------------------------------

## Functional Area {#functional-area .LS_Heading-3}

Cost of sales accounting compares the sales revenues for an accounting period with the costs involved with the production of the sold products. The expenses are allocated to the commercial functional areas (for example, manufacturing, sales and distribution, administration and marketing). Expenses and revenues that cannot be assigned to the functional areas are reported in further profit and loss items, sorted according to expense and revenue type

[Home Control will have the below list of Functional Areas:]{.mark}

  ----------------------------------------
  Functional Area   FunctArea text
  ----------------- ----------------------
  1000              Manufacturing

  2000              Sales

  3000              G&A

  5000              R&D
  ----------------------------------------

## Chart of Accounts {#chart-of-accounts .LS_Heading-3}

While not normally considered an organizational unit, the Chart of Accounts (COA) is mapped to each Company Code. The COA contains the G/L Accounts used for postings in the Company Code during daily activities. Financial Accounting and Controlling both use this COA. The Operating COA is an organized list of all general ledger master records (natural accounts) that are required for one or more Company Codes. Not all accounts defined within the COA must be used by every assigned Company Code.

Note: the operating chart of accounts is most often referred to as simply the 'Chart of Accounts'.

SAP delivered Chart of Accounts YCOA will be used for Home Control. For more details relating to the COA, please see design document 'HC_SAP_DD_FI03_General Ledger Processing'. Please find below attached the Chart of Accounts used for Home Control:

![](media/media/image3.emf)

## Parallel ledger {#parallel-ledger .LS_Heading-3}

The following are ledger details with local currency and fiscal year setup in Home Control

+--------------------------------------------------+------------------------------------------+---------------+---------------+
| **Company code**                                 | **Currency**                             | **Ledger 0L** | **Ledger 2L** |
+==================================================+==========================+===============+===============+===============+
| Leading                                          | 　                       | 　            | X             | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| Corporate Accounting Princ.                      | 　                       | 　            | IFRS          | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **SG21 Home Control Singapore Pte Ltd**          | 10 Company Code Currency | SGD           | IFRS (K4)     | SGAP(K4)      |
|                                                  +--------------------------+---------------+---------------+---------------+
|                                                  | 30 Group Currency        | USD           | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           |                          |               | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | Functional Currency      | 30            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **CN13 HCS (Suzhou) Limited**                    | 10 Company Code Currency | CNY           | IFRS (K4)     | CNAP (K4)     |
|                                                  +--------------------------+---------------+---------------+---------------+
|                                                  | 30 Group Currency        | USD           | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | Functional Currency      | 10            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | 　                       | 　            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **CN17 Home Control Solutions (Suzhou) Limited** | 10 Company Code Currency | CNY           | IFRS (K4)     | CNAP (K4)     |
|                                                  +--------------------------+---------------+---------------+---------------+
|                                                  | 30 Group Currency        | USD           | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | Functional Currency      | 10            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | 　                       | 　            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **US10 Premium Home Control Solutions LLC**      | 10 Company Code Currency | USD           | IFRS (K4)     | USAP (K4)     |
|                                                  +--------------------------+---------------+---------------+---------------+
|                                                  | 30 Group Currency        | USD           | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | Functional Currency      | 10            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | 　                       | 　            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **BE10 Home Control Europe NV**                  | 10 Company Code Currency | EUR           | IFRS (K4)     | BEAP(K4)      |
|                                                  +--------------------------+---------------+---------------+---------------+
|                                                  | 30 Group Currency        | USD           | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | Functional Currency      | 10            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | 　                       | 　            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **HCIL Home Control International Limited**      | 10 Company Code Currency | KYD           | IFRS (K4)     | IFRS (K4)     |
|                                                  +--------------------------+---------------+---------------+---------------+
|                                                  | 30 Group Currency        | USD           | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           |                          |               | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **　**                                           | Functional Currency      | 30            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| **BR10 Omni Remotes Do Brasil Ltda**             | 10 Company Code Currency | BRL           | IFRS (K4)     | BRAP(K4)      |
|                                                  +--------------------------+---------------+---------------+---------------+
|                                                  | 30 Group Currency        | USD           | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+
| 　                                               | Functional Currency      | 10            | 　            | 　            |
+--------------------------------------------------+--------------------------+---------------+---------------+---------------+

## Account Group (GL Account) {#account-group-gl-account .LS_Heading-3}

**Account Groups for Operating/group/county Chart of Accounts**

  -------------------------------------------------------------------------------------------
  **ChAc**   **AcGp**   **From acct**   **To account**   **Name**
  ---------- ---------- --------------- ---------------- ------------------------------------
  CCOA       GEN        0               ZZZZZZZZZZ       　

  HCOA       AS         0               999999           Asset accounts

  ~~HCOA~~   ~~ASGW~~   ~~60000~~       ~~99999~~        ~~Asset accounts - Goodwill~~

  ~~HCOA~~   ~~ATPO~~   ~~0~~           ~~9999999~~      ~~　~~

  ~~HCOA~~   ~~BOE~~    ~~3000000~~     ~~3999999~~      ~~Cash/Bank for Bill of Exchange~~

  HCOA       CASH       3000000         3999999          Cash and Bank Accounts

  HCOA       FA         0               9999999          Local fiscal accounts

  HCOA       GEN        0               9999999          G/L accounts

  HCOA       GL         0               5999999          Balance Sheet Accounts

  HCOA       GLPA       0               5999999          Balance Sheet Acc - Post Autom

  ~~HCOA~~   ~~IFPL~~   ~~700000~~      ~~999999~~       ~~IFRS Accounts P&L~~

  ~~HCOA~~   ~~IFRS~~   ~~700000~~      ~~999999~~       ~~IFRS Accounts~~

  HCOA       MAT        1000000         9999999          Material accounts

  HCOA       PL         5990000         9999999          Profit and loss accounts

  ~~HCOA~~   ~~PLPA~~   ~~6000000~~     ~~9999999~~      ~~P&L Accounts - Post Aut. Only~~

  HCOA       RECO       1000000         5999999          Reconciliation accounts AP/AR

  ~~HCOA~~   ~~TEMP~~   ~~0~~           ~~5999999~~      ~~Temporary - do not use -~~

  ~~HCOA~~   ~~ZAS~~    ~~C~~           ~~C999999~~      [　]{.mark}

  ~~HCOA~~   ~~ZGL~~    ~~C~~           ~~C5999999~~     [　]{.mark}

  ~~HCOA~~   ~~ZPL~~    ~~C5990000~~    ~~C9999999~~     [　]{.mark}
  -------------------------------------------------------------------------------------------

## Fiscal Year Variant  {#fiscal-year-variant .LS_Heading-3}

The fiscal year variant determines the number of posting periods and special periods per fiscal year. Home Control follows a calendar year-independent fiscal year variant and would use "K4", the fiscal year commencing on 1 January and ending on 31 December. K4 comprises 12 posting periods and 4 special periods. Leading ledger "0L" of all Home Control entities as well as all country ledgers will have K4 fiscal year variant.

Home Control SAP Accounting periods are as follows:

- Period 01-12: Regular results

- Period 13: Used for Group Audit Adjustments

- Period 14: Used for local Statutory reporting adjustments

- Period 15: Used for local Fiscal reporting adjustments

- Period 16: Exclusively used for reclassification in MRU/ORU (to be done before Balance Carryforward)

## Exchange Rate Type {#exchange-rate-type .LS_Heading-3}

More than one exchange rate types are required to be maintained for different purposes/transactions on a same date.

Home Control would define and maintain the following exchange rates:

1\. 'M' - average exchange rate will be used for day to day transactions.

2\. 'ME' -- month end rate for foreign currency revaluation will be used as the next month activity rate

3\. 'ZE' -- China year end rate

4\. 'P' -- Planning rate (use for yearly/quarterly CO planning)

## Document Type {#document-type .LS_Heading-3}

Document types are created in Financial Accounting for customer, vendor, assets, materials and general ledger business transactions. Document types differentiate business transactions, control document filing and numbering. Number range would be determined and assigned to each document type to facilitate numbering control by document range.

## Bank Keys {#bank-keys .LS_Heading-3}

Bank Key is a bank directory of specific country. Bank master needs to be set up to facilitate payment processing. General information on the banks such as the bank's country, address, branch and SWIFT code are maintained using bank masters. In SAP, bank master data is required in vendor / customer and house banks to identify bank branch details.

**Naming convention:**

- Bank key in SG: 7 digits, Bank code (4 digits) +Branch code (3 digits)

- Bank key in CN: 11 digits, Swift code (first 4 digits) +Region Code (3 digits) +sequence number (3 digits) + C (CNY)/E (Foreign)

- Bank Key in BE: 3digits, IBAN number (from the 5^th^ digit selecting 3 digits of IBAN)

- Bank Key in US: 9digits, ABA Routing No.

![](media/media/image4.emf)

## Trading partner {#trading-partner .LS_Heading-3}

Intercompany and related parties will be represented as trading partners which are to be created and assigned in business partner master records.

When an intercompany customer or vendor is posted in a document, the 'trading partner' will be copied into the receivables or payable entry and into the offsetting entry too. As a result, the partner data will be available in the consolidation for both of the elimination of intercompany payables and receivables from the balance sheet and elimination of intercompany revenue and expense from the income statement.

List of trading partners at Home Control

  ---------------------------------------------------------------
  **Trading partner**   **Description**
  --------------------- -----------------------------------------
  SG21                  Home Control Singapore Pte Ltd 

  CN13                  HC (Suzhou) Limited 

  CN17                  Home Control Solutions (Suzhou) Limited

  US10                  Premium Home Control Solutions LLC 

  BE10                  Home Control Europe NV 

  HCIL                  Home Control International Limited

  BR10                  Omni Remotes Do Brasil Ltda
  ---------------------------------------------------------------

1.  

    1.  

## Business Process for  Manage GL Master Records {#business-process-for-manage-gl-master-records .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| Process Step                                                                                                                                                | Business Role                | Transaction/App                                                                                                                    | Expected Results                          |
+=============================================================================================================================================================+==============================+====================================================================================================================================+===========================================+
| 1.  Business Unit requests to create new or change the existing GL Accounts.                                                                                | N/A                          | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 2.  If the GL Account does exist in Co Code, then inform requestor; otherwise, GL administrator checks at COA level.                                        | GL administrator             | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 3.  GL administrator extends GL Account at company code level                                                                                               | GL administrator             | Manage G/L Account Master Data                                                                                                     | Extended GL Account at company code level |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 4.  If GL account does not exist at COA level, GL administrator asks Business unit requestor to give business justification for new GL account at COA level | GL administrator             | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 5.  GL administrator fills up GL Maintenance Form/ Request form and send request for review                                                                 | GL administrator             | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 6.  If the request for new account creation at COA level is rejected, GL administrator returns to requester/BU                                              | GL administrator             | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 7.  If the request form is approved, GL administrator sends approved request form to GL administrator central                                               | GL Administration -- central | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 8.  GL Administration -- central creates GL Account at COA level                                                                                            | GL Administration -- central | Manage G/L Account Master Data                                                                                                     | GL Account is created at COA level        |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 9.  GL Administration -- central changes GL Account at COA level                                                                                            | GL Administration -- central | Manage G/L Account Master Data                                                                                                     | GL Account is changed at COA level        |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 10. GL Administration -- central verifies GL account creation                                                                                               | GL Administration -- central | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 11. Assign GL account to Financial Statement version                                                                                                        | GL Administration -- central | Accounting-\>General Ledger-\> Chart of Accounts-\> Chart of Accounts & Financial Statements-\>Define Financial Statement Versions | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+
| 12. GL Administration -- central informs BU GL administrator about new GL account                                                                           | GL Administration -- central | N/A                                                                                                                                | N/A                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------+

## Manage Posting in GL and Parallel Ledger  {#manage-posting-in-gl-and-parallel-ledger .LS_Heading-3}

![](media/media/image6.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+---------------------------------------------------------------------------------------------------------------------------+--------------------------------+------------------------+---------------------------------------------------------------------------+
| Process Step                                                                                                              | Business Role                  | Transaction/App        | Expected Results                                                          |
+===========================================================================================================================+================================+========================+===========================================================================+
| 1.  Finance receives supporting documents for GL Postings                                                                 | GL Processing Officer          | N/A                    | N/A                                                                       |
+---------------------------------------------------------------------------------------------------------------------------+--------------------------------+------------------------+---------------------------------------------------------------------------+
| 2.  GL processing officer makes GL postings if all supporting documents are okay.                                         | GL Processing Officer          | Manage Journal Entries | Journal Entry is posted. Posting document will update G/L account balance |
|                                                                                                                           |                                |                        |                                                                           |
| Posting document will update G/L account balance.                                                                         |                                |                        |                                                                           |
+---------------------------------------------------------------------------------------------------------------------------+--------------------------------+------------------------+---------------------------------------------------------------------------+
| 3.  Finance Manager checks the GL documents and postings                                                                  | Finance Manager (GL Reporting) | Manage Journal Entries | Journal Entry is posted.                                                  |
+---------------------------------------------------------------------------------------------------------------------------+--------------------------------+------------------------+---------------------------------------------------------------------------+
| 4.  For any error in GL account, amount or cost center, etc., Finance Manger notifies the poster to reverse the documents | Finance Manager                | N/A                    | N/A                                                                       |
+---------------------------------------------------------------------------------------------------------------------------+--------------------------------+------------------------+---------------------------------------------------------------------------+
| 5.  The poster reverses the documents in case there is any GL error                                                       | GL Processing Officer          | Manage Journal Entries | Journal Entry is reversed.                                                |
+---------------------------------------------------------------------------------------------------------------------------+--------------------------------+------------------------+---------------------------------------------------------------------------+
| 6.  If the all the GL documents are okay, Finance Manager will sign in the document list.                                 | Finance Manager                | N/A                    | N/A                                                                       |
+---------------------------------------------------------------------------------------------------------------------------+--------------------------------+------------------------+---------------------------------------------------------------------------+

## Bank Master Data  {#bank-master-data .LS_Heading-3}

![](media/media/image7.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+
| Process Step                                 | Business Role   | Transaction/App                                       | Expected Results                         |
+==============================================+=================+=======================================================+==========================================+
| 1.  Request for creation of new bank master  | N/A             | N/A                                                   | N/A                                      |
+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+
| 2.  Check whether bank master already exists | Bank accountant | Manage Banks-Master Data Manage Banks-Cash Management | Check whether bank master already exists |
|                                              |                 |                                                       |                                          |
|                                              |                 | Manage Bank Accounts                                  |                                          |
+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+
| 3.  Verify request                           | Bank accountant | N/A                                                   | N/A                                      |
+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+
| 4.  Create bank master data                  | Bank accountant | Manage Banks-Master Data Manage Banks-Cash Management | Bank Accounts is created.                |
|                                              |                 |                                                       |                                          |
|                                              |                 | Manage Bank Accounts                                  |                                          |
+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+
| 5.  Change bank master if required           | Bank accountant | Manage Banks-Master Data Manage Banks-Cash Management | Bank Accounts is changed.                |
|                                              |                 |                                                       |                                          |
|                                              |                 | Manage Bank Accounts                                  |                                          |
+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+
| 6.  If rejected, inform requestor            | Bank accountant | N/A                                                   | N/A                                      |
+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+
| 7.  Inform relevant parties                  | Bank accountant | N/A                                                   | N/A                                      |
+----------------------------------------------+-----------------+-------------------------------------------------------+------------------------------------------+

## Month End Closing Operations  {#month-end-closing-operations .LS_Heading-3}

![](media/media/image8.emf)

![](media/media/image9.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| Process Step                                                  | Business Role         | Transaction/App                                            | Expected Results                                              |
+===============================================================+=======================+============================================================+===============================================================+
| 1.  List all GL Parked Documents and Analysis                 | GL Executive Periodic | Manage G/L Account Master Data                             | List all GL Parked Documents                                  |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 2.  Run Depreciation                                          | AA Executive Periodic | Schedule Asset Accounting Jobs                             | The asset depreciation has been completed.                    |
|                                                               |                       |                                                            |                                                               |
|                                                               |                       | Select template Depreciation Posting Run                   |                                                               |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 3.  Perform GR/IR Auto Clearing                               | GL Executive Periodic | Schedule General Ledger Jobs                               | GR/IR Clearing                                                |
|                                                               |                       |                                                            |                                                               |
|                                                               |                       | Select template GR/IR Automatic Clearing With Extended OIM |                                                               |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 4.  Maintain Exchange rate (both M and ME rates)              | FI Treasury Officer   | Currency Exchange Rates                                    | Exchange rate is created                                      |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 5.  Open MM posting period for the next month                 | GL Executive Periodic | Close Periods                                              | Period for the next month is opened                           |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 6.  Open FI posting period (GL/AP/AR/Fixed Assets/ Inventory) | GL Executive Periodic | Manage Posting Periods                                     | FI posting period is opened                                   |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 7.  Reconcile Bank Statement                                  | Bank Admin            | Clear Open Items                                           | Reconcile Bank Statement                                      |
|                                                               |                       |                                                            |                                                               |
|                                                               |                       | Automatic Clearing                                         |                                                               |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 8.  GL Periodic Postings                                      | GL Executive Periodic | Manage Journal Entries                                     | Recurring Journal Entries are posted                          |
|                                                               |                       |                                                            |                                                               |
|                                                               |                       | Manage Recurring Journal Entries                           |                                                               |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 9.  AR/AP/GL Adjustment                                       | GL Executive Periodic | Journal Entries are posted                                 | Journal Entries are posted                                    |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 10. Open Item Clearing                                        | GL Executive Periodic | Clear Open Items                                           | Open Items are cleared                                        |
|                                                               |                       |                                                            |                                                               |
|                                                               |                       | Automatic Clearing                                         |                                                               |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 11. Foreign Currency Revaluation                              | GL Executive Periodic | Schedule General Ledger Jobs                               | Journal Entries for Foreign Currency Revaluation are posted   |
|                                                               |                       |                                                            |                                                               |
|                                                               |                       | select the template Advanced Foreign Currency Valuation    |                                                               |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 12. Close FI Posting Period (AP/AR/Fixed Assets/ Inventory)   | GL Executive Periodic | Manage Posting Periods                                     | FI Posting Periods (AP/AR/Fixed Assets/ Inventory) are closed |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 13. GL Adjustment                                             | GL Executive Periodic | Manage G/L Account Master Data                             | Journal Entries are posted                                    |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 14. Close FI Posting Period for GL                            | GL Executive Periodic | Manage Posting Periods                                     | FI GLPosting Periods is closed                                |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+
| 15. Run reports                                               | GL Reporting          | Balance Sheet / Income Statement China                     | Reports are generated                                         |
+---------------------------------------------------------------+-----------------------+------------------------------------------------------------+---------------------------------------------------------------+

## Manage Balance Carryforward {#manage-balance-carryforward .LS_Heading-3}

![](media/media/image10.emf)

## Business Process Steps {#business-process-steps-4 .LS_Heading-3}

+---------------------------------------------------------------+-----------------------+----------------------------------------------------------+-----------------------------------------------------------------------------------------+
| Process Step                                                  | Business Role         | Transaction/App                                          | Expected Results                                                                        |
+===============================================================+=======================+==========================================================+=========================================================================================+
| 1.  Transfer of P&L Accounts Balance to Retained Earning A/c  | GL executive periodic | Schedule General Ledger Jobs                             | P&L Accounts Balance Transfer to Retained Earning A/c                                   |
|                                                               |                       |                                                          |                                                                                         |
|                                                               |                       | Select the template Balance Carryforward                 |                                                                                         |
+---------------------------------------------------------------+-----------------------+----------------------------------------------------------+-----------------------------------------------------------------------------------------+
| 2.  Carry Forward of Balance Sheet Items-GL Balances          | GL executive periodic | Schedule General Ledger Jobs                             | Balance Sheet Items-GL Balances Carry Forward to the next year                          |
|                                                               |                       |                                                          |                                                                                         |
|                                                               |                       | Select the template Balance Carryforward                 |                                                                                         |
+---------------------------------------------------------------+-----------------------+----------------------------------------------------------+-----------------------------------------------------------------------------------------+
| 3.  Review of Opening Balances in the New Fiscal Year         | GL executive periodic | Display G/L Account Balances                             | Query G/L Account Balances                                                              |
|                                                               |                       |                                                          |                                                                                         |
|                                                               |                       | Display G/L Account Balances-Summary/Journal Entry Views |                                                                                         |
+---------------------------------------------------------------+-----------------------+----------------------------------------------------------+-----------------------------------------------------------------------------------------+
| 4.  Close previous asset fiscal year and open new Fiscal Year | AA Executive periodic | Make Company Code Settings Asset Accounting-Specific     | previous asset fiscal year is closed and new fiscal year for Asset accounting is opened |
+---------------------------------------------------------------+-----------------------+----------------------------------------------------------+-----------------------------------------------------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- The central task of general ledger accounting is to provide a comprehensive overview of external accounting and accounts.

- By recording all business transactions, including primary postings and settlements from internal accounting, in a system that is fully integrated with all the other operational areas of a company, you ensure accuracy and completeness for accounting data.

- General ledger accounting serves as a complete record of all business transactions, providing a centralized, current reference for the rendering of accounts. Actual individual transactions are reviewed with real-time processing, displaying the original documents, line items, and transaction figures at various levels (such as account information, journals, totals, transaction figures, and balance sheets).

- Post general ledger account documents

- Display the document journal

- Display G/L balances (list)

- Perform recurring entries

- Maintain accounts with automatic and manual clearing

- Perform day-end closing

- Perform month-end closing

- Perform year-end closing

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- Journal Entries do not require approval in SAP system.

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Journal Entries list {#journal-entries-list .LS_Heading-3}

  --------------------------------------------------------------------------
  **Document Type**   **Description**        **Comments**
  ------------------- ---------------------- -------------------------------
                      Journal Entries list   List of voucher details

  **​​文档类型​​**        **​​描述​​**               **​​注释​​**

  ​**​**                凭证清单               凭证的明细列表
  --------------------------------------------------------------------------

## Journal Entries {#journal-entries .LS_Heading-3}

  ----------------------------------------------------------------------
  **Document Type**   **Description**    **Comments**
  ------------------- ------------------ -------------------------------
                      Journal Entries    Journal Entries Form

  **​​文档类型​​**        **​​描述​​**           **​​注释​​**

  ​**​**                凭证               凭证表单
  ----------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Default document number ranges will be used for Journal Entries.

- The cash flow statement is prepared using the direct method, and the issue of splitting cash flow items during batch AP payments needs to be resolved.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Dependencies on Financial Sub-modules

<!-- -->

- Accounts Receivable: Data such as customer collections and invoice write-offs need to be synchronized to the general ledger to update accounts such as revenue and accounts receivable.

- Accounts Payable: Data such as supplier payments and invoice verification need to be transmitted to the general ledger to update accounts such as costs and accounts payable.

- Fixed Assets: Information such as asset acquisition, depreciation accrual, and disposal needs to be synchronized to the general ledger, affecting accounts such as original asset value, accumulated depreciation, and expense accounts.

- Cash Management: Bank statements and records of fund receipts and payments need to be reconciled with the general ledger to ensure that the balances of cash and bank deposit accounts are consistent.

<!-- -->

- Dependencies on Business Operations Departments

<!-- -->

- Sales Department: Sales orders, shipment records, etc., need to be converted into financial revenue data and transmitted to the general ledger.

- Purchasing Department: Purchase orders and receipt records need to be associated with accounts payable, and ultimately reflected in the cost or asset accounts of the general ledger.

- Production Department: Cost accumulation during production (such as raw material consumption and labor costs) needs to be transmitted to the general ledger through the cost accounting module to update production cost and inventory-related accounts.

- Human Resources Department: Data such as employee salaries, benefits, and social security need to be recorded in expense or liability accounts through the general ledger.

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

+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| **Business Role**            | **Role Description**                                                                          | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+==============================+===============================================================================================+================================+==========================+
| AA Executive Periodic        | Role includes the following key system tasks:                                                 | Std Roles                      | - BR_AA_ACCOUNTANT       |
|                              |                                                                                               |                                |                          |
|                              | - Run Depreciation                                                                            |                                |                          |
|                              |                                                                                               |                                |                          |
|                              | - Close previous asset fiscal year and open new Fiscal Year                                   |                                |                          |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| Bank accountant              | - Maintain Bank Master Data                                                                   | Std Roles                      | - BR_CASH_SPECIALIST     |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| Bank Admin                   | - Reconcile Bank Statement                                                                    | Std Roles                      | - BR_CASH_MANAGER        |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| FI Treasury Officer          | - Maintain Exchange rate                                                                      | Std Roles                      | - BR_GL_ACCOUNTANT       |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| Finance Manager              | - checks the GL documents and postings                                                        | Std Roles                      | - BR_GL_ACCOUNTANT       |
|                              |                                                                                               |                                |                          |
|                              | - sign in the document list                                                                   |                                |                          |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| GL administrator             | - Extends GL Account at company code level                                                    | Std Roles                      | BR_GL_ACCOUNTANT         |
|                              |                                                                                               |                                |                          |
|                              | - fills up GL Maintenance Form/ Request form and send request to GL Administration -- central |                                |                          |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| GL Administration -- central | - Maintain GL Account at COA level                                                            | Std Roles                      | BR_GL_ACCOUNTANT         |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| GL Processing Officer        | - Receives supporting documents for GL Postings                                               | Std Roles                      | BR_GL_ACCOUNTANT         |
|                              |                                                                                               |                                |                          |
|                              | - Create or reverse the journal entries                                                       |                                |                          |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| GL Executive Periodic        | - Perform the Month End Closing process                                                       | Std Roles                      | BR_GL_ACCOUNTANT         |
|                              |                                                                                               |                                |                          |
|                              | - Manage Balance Carryforward                                                                 |                                |                          |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| GL Reporting                 | - Run reports                                                                                 | Std Roles                      | BR_GL_ACCOUNTANT         |
+------------------------------+-----------------------------------------------------------------------------------------------+--------------------------------+--------------------------+

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

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **SAP App**                                                **Description / Usage**
  ---------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Display G/L Account Balances                               Used to query general ledger account balances, supporting filtering by dimensions such as period, account range, and company code, and displaying the opening balance, current period movements (debit/credit), and closing balance of accounts.

  Display Line Items in General Ledger                       Displays detailed line items in the general ledger, which can be filtered by conditions such as account, document type, and date. Each record contains detailed information including document number, posting date, amount, description, and associated business objects (e.g., invoices, payment orders). This facilitates tracing the source of general ledger data and specific business backgrounds, and supports reconciliation and auditing.

  Display G/L Account Balances Summary/Journal Entry Views   It provides summary views and journal entry views of general ledger account balances. The summary view presents an overview of account balances (such as total balances classified by account groups); the journal entry view is linked to specific accounting documents, enabling drill-through queries from balances to detailed entries, which takes into account both macro control and micro traceability of general ledger data.

  Balance Sheet / Income Statement China                     A financial reporting tool specifically designed for Chinese accounting standards, which automatically generates balance sheets and income statements that comply with Chinese regulations. It supports displaying data in formats required by Chinese accounting systems, including statutory report items, detailed account mappings, and information needed for report notes, meeting the compliance requirements of domestic financial reporting and tax declaration.
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

+----------------------------------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                                                    |
+--------------------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**                             | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|                                      |                   |                           |                            | (# items)**   |                |
+======================================+===================+===========================+============================+===============+================+
| GL account balance and openline item | ECC               | Low                       | Med                        | TBD           |                |
|                                      |                   |                           |                            |               |                |
| 总账科目余额及未清项                 |                   |                           |                            |               |                |
+--------------------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|                                      |                   |                           |                            |               |                |
+--------------------------------------+-------------------+---------------------------+----------------------------+---------------+----------------+

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

+---------------------------------------------------------------------------------------------------------------------------------+
| **Forms**                                                                                                                       |
+----------------------+------------------------------------+-------------------+-------------------+-----------------------------+
| **Form**             | **Description**                    | **Complexity**    | **In Scope**      | **Comments**                |
+======================+====================================+===================+===================+=============================+
| Journal Entries list | List of voucher details            | Med               | Yes               |                             |
+----------------------+------------------------------------+-------------------+-------------------+-----------------------------+
| Journal Entries      | Custom Journal Entries output form | Med               | Yes               | New Form need to be created |
+----------------------+------------------------------------+-------------------+-------------------+-----------------------------+
| **表单​​**             | **​​描述​​**                           | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**                    |
+----------------------+------------------------------------+-------------------+-------------------+-----------------------------+
| ​​凭证清单             | 凭证清单                           | 中等              | 是                |                             |
+----------------------+------------------------------------+-------------------+-------------------+-----------------------------+
| 凭证                 | 凭证打印表单                       | 中等              | 是                | 需新建表单                  |
+----------------------+------------------------------------+-------------------+-------------------+-----------------------------+

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
