**Billing Process**

**开票凭证流程**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_SD04 -- SD Billing Processing**

**Version 2.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

        Warner Yu                SD Lead                21/08/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [6](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [6](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [6](#design-document-approval-options)](#design-document-approval-options)

[2. Standard Customer Billing [6](#standard-customer-billing)](#standard-customer-billing)

[2.1 Purpose [6](#purpose)](#purpose)

[2.2 Business Reason [7](#business-reason)](#business-reason)

[2.3 Business Benefits [7](#business-benefits)](#business-benefits)

[3. Inter Company Billing [7](#inter-company-billing)](#inter-company-billing)

[3.1 Purpose [7](#purpose-1)](#purpose-1)

[3.2 Business Reason [7](#business-reason-1)](#business-reason-1)

[3.3 Business Benefits [8](#business-benefits-1)](#business-benefits-1)

[4. Credit/Debit Memo [8](#creditdebit-memo)](#creditdebit-memo)

[4.1 Purpose [8](#purpose-2)](#purpose-2)

[4.2 Business Reason [8](#business-reason-2)](#business-reason-2)

[4.3 Business Benefits [8](#business-benefits-2)](#business-benefits-2)

[5. Golden Tax System [8](#golden-tax-system)](#golden-tax-system)

[5.1 Purpose [8](#purpose-3)](#purpose-3)

[5.2 Business Reason [9](#business-reason-3)](#business-reason-3)

[5.3 Business Benefits [9](#business-benefits-3)](#business-benefits-3)

[6. Process Scope Design [10](#process-scope-design)](#process-scope-design)

[6.1 Business Process for Standard Customer Billing流程图 [10](#business-process-for-standard-customer-billing流程图)](#business-process-for-standard-customer-billing流程图)

[6.1.1 Business Process Steps [10](#business-process-steps)](#business-process-steps)

[6.2 HC Functional Requirements [11](#hc-functional-requirements)](#hc-functional-requirements)

[6.3 HC Delegation Of Authority [12](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[6.4 Standard Documents / Settings [12](#standard-documents-settings)](#standard-documents-settings)

[6.4.1 Billing Dcoument [12](#billing-dcoument)](#billing-dcoument)

[6.5 Design Considerations / Key Assumptions [12](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[6.6 Cross Functional Integration Dependencies [12](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[7. Process Scope Design [13](#process-scope-design-1)](#process-scope-design-1)

[7.1 Business Process for Intercompany Billing 流程图 [13](#business-process-for-intercompany-billing-流程图)](#business-process-for-intercompany-billing-流程图)

[7.1.1 Business Process Steps [13](#business-process-steps-1)](#business-process-steps-1)

[7.2 HC Functional Requirements [15](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[7.3 HC Delegation Of Authority [15](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[7.4 Standard Documents / Settings [15](#standard-documents-settings-1)](#standard-documents-settings-1)

[7.5 Design Considerations / Key Assumptions [15](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[7.6 Cross Functional Integration Dependencies [15](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[7.7 Support / Closing Considerations [16](#support-closing-considerations)](#support-closing-considerations)

[8. Process Scope Design [16](#process-scope-design-2)](#process-scope-design-2)

[8.1 Business Process for Credit/Debit Memo 流程图 [16](#business-process-for-creditdebit-memo-流程图)](#business-process-for-creditdebit-memo-流程图)

[8.1.1 Stnadard Business Process Steps [16](#stnadard-business-process-steps)](#stnadard-business-process-steps)

[8.2 HC Functional Requirements [17](#hc-functional-requirements-2)](#hc-functional-requirements-2)

[8.3 HC Delegation Of Authority [17](#hc-delegation-of-authority-2)](#hc-delegation-of-authority-2)

[8.4 Standard Documents / Settings [18](#standard-documents-settings-2)](#standard-documents-settings-2)

[8.5 Design Considerations / Key Assumptions [18](#design-considerations-key-assumptions-2)](#design-considerations-key-assumptions-2)

[8.6 Cross Functional Integration Dependencies [18](#cross-functional-integration-dependencies-2)](#cross-functional-integration-dependencies-2)

[8.7 Support / Closing Considerations [18](#support-closing-considerations-1)](#support-closing-considerations-1)

[9. Process Scope Design [18](#process-scope-design-3)](#process-scope-design-3)

[9.1 Business Process for GTS 流程图 [18](#business-process-for-gts-流程图)](#business-process-for-gts-流程图)

[9.1.1 GTS Business Process Steps [18](#gts-business-process-steps)](#gts-business-process-steps)

[9.1.2 Cancel GTS Business Process Steps [19](#cancel-gts-business-process-steps)](#cancel-gts-business-process-steps)

[9.2 HC Functional Requirements [20](#hc-functional-requirements-3)](#hc-functional-requirements-3)

[9.3 HC Delegation Of Authority [20](#hc-delegation-of-authority-3)](#hc-delegation-of-authority-3)

[9.4 Standard Documents / Settings [20](#standard-documents-settings-3)](#standard-documents-settings-3)

[9.5 Design Considerations / Key Assumptions [20](#design-considerations-key-assumptions-3)](#design-considerations-key-assumptions-3)

[9.6 Cross Functional Integration Dependencies [20](#cross-functional-integration-dependencies-3)](#cross-functional-integration-dependencies-3)

[9.7 Support / Closing Considerations [21](#support-closing-considerations-2)](#support-closing-considerations-2)

[10. Authorization Roles [21](#authorization-roles)](#authorization-roles)

[10.1 rization Roles [21](#rization-roles)](#rization-roles)

[11. Document Types and Document Flow [22](#document-types-and-document-flow)](#document-types-and-document-flow)

[12. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [22](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[12.1 Reports [22](#reports)](#reports)

[12.1.1 Standard Reports [22](#standard-reports)](#standard-reports)

[12.1.2 HC Requested Reports [23](#hc-requested-reports)](#hc-requested-reports)

[12.2 Interfaces [23](#interfaces)](#interfaces)

[12.3 Conversions [23](#conversions)](#conversions)

[12.4 Enhancements [24](#enhancements)](#enhancements)

[12.5 Forms [24](#forms)](#forms)

[12.6 Workflows [25](#workflows)](#workflows)

[13. Legend for Process Flow [26](#legend-for-process-flow)](#legend-for-process-flow)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       28/07/2025

       2.0                 Change after reviewing.                 15/08/2025

                                                              
  ------------- --------------------------------------------- --------------------

# Guidelines {#guidelines .LS_Heading-1}

## Design Document Approval Overview {#design-document-approval-overview .LS_Heading-3}

The SAP Implementation Project Design Documents are the result of the Fit / Gap workshops.  All Project Design Documents must be reviewed and approved by the Home Control team to confirm we have captured the appropriate requirements as well as gaps, proposed solutions, and RICEFW objects​ from the workshops.

SAP Design Documents are living, breathing documents. As the SAP system is configured, tested, modified, and approved, the design documents may be updated to reflect the final design​.

Home Control Team Leads create the original design documents​. Should Home Control decide to update the Design Documents, it is up to Home Control to perform the updates.

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

# Standard Customer Billing {#standard-customer-billing .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

Invoice (billing document) represents the final step in the sales process chain. An important part of invoice is the integration with Financial Accounting. This allows documents to be created automatically in Financial Accounting and Controlling when billing documents created.

## Business Reason {#business-reason .LS_Heading-3}

- Mainly used to generate financial documents and handle customers\' accounts receivable.

- Billing Document is the basis of Golden Tax invoice.

## Business Benefits {#business-benefits .LS_Heading-3}

- Automation and efficiency improvement

- Process visualization

# Inter Company Billing {#inter-company-billing .LS_Heading-1}

2.  

<!-- -->

1.  

##  Purpose {#purpose-1 .LS_Heading-3}

This scenario shows how sales are processed across company codes.

A customer orders goods from their vendor's sales organization. The vendor has a production / warehouse plant that belongs to a different company code. The goods are produced / contained here and delivered from the production / warehouse plant directly to the customer.

**Focus:**

- Delivering plant belongs to a different company code

- Direct delivery from delivering plant to customer

- Customer invoice and intercompany billing document

- Intercompany billing document automatically creates inter-company vendor invoice in accounts payable

- Internal transfer prices

Customer XXXXXX sends a purchase order to their vendor's sales organization. A standard order is created here with the production/warehouse plant from a different company code, as a delivering plant.

The goods are delivered from the production / warehouse plant directly to the customer.

The delivery is billed twice, once to create the customer invoice and again to carry out intercompany billing. The Intercompany billing document automatically creates inter-company vendor invoice in accounts payable.

The customer pays their invoice by transferring the amount to the bank account. A manual account statement is posted, and the open item on the customer's account is cleared.

## Business Reason {#business-reason-1 .LS_Heading-3}

With automatic vendor invoice generation from the intercompany billing document, the accounts payable in the selling company is automatically and immediately realized, that is, the amount due to the supplying company for supply of goods to the customer.

## Business Benefits {#business-benefits-1 .LS_Heading-3}

- Business process integration

- Standardize transaction management

- Optimize resource allocation

- Collaborative data sharing

# Credit/Debit Memo {#creditdebit-memo .LS_Heading-1}

3.  

<!-- -->

2.  

## Purpose {#purpose-2 .LS_Heading-3}

In SAP, Debit/Credit memos are mainly used to handle price adjustments, returns, or special transaction scenarios in sales operations.\
HC mostly handles with CM related business.

The Credit Memo process is used to apply a credit to a customer account once company have determined that a customer has been overcharged as a result of a pricing or sales tax rate error. An Invoice Correction request is then created with the amount to be credited, and placed on a billing block for review. It must then be released to become billing relevant, and appear on the billing due list. The periodic billing process creates a credit memo to be sent to the customer, and posts an accounting document.

## Business Reason {#business-reason-2 .LS_Heading-3}

In actual operations, there are often situations such as discovering incorrect prices after receiving payment, or needing to refund customers or collect additional payments from them for other reasons; or cases where customers need a small amount of materials that cannot be handled through the method of selling materials, etc. All these can be processed via debit/credit memos (debit memos are used for collecting additional payments from customers, and credit memos are used for refunding customers).\
HC mostly handles with CM related business.

A Credit Memo Request is created with the amount to be credited to the Cusotmer while the goods are retruned to the company with a reason for rejection. Periodic billing process creates a Credit Memo to be sent to the customer, and posts an accounting document.

## Business Benefits {#business-benefits-2 .LS_Heading-3}

- Integrate Credit /Debit Memo processing in the system

# Golden Tax System {#golden-tax-system .LS_Heading-1}

4.  

<!-- -->

3.  

## Purpose {#purpose-3 .LS_Heading-3}

The Golden Tax System is mainly used to handle the issuance of Chinese VAT invoices, tax calculation, and compliant filing, ensuring that enterprises\' tax processes comply with the requirements of Chinese tax laws.

- VAT Invoice Management

- Tax Calculation and Posting

- Compliant Filing and Risk Control

## Business Reason {#business-reason-3 .LS_Heading-3}

GTS is an important part of China\'s tax administration system, mainly used for the issuance and management of VAT invoices. As an enterprise resource planning (ERP) system, the SAP system needs to interface with the Golden Tax System to meet tax compliance requirements.

## Business Benefits {#business-benefits-3 .LS_Heading-3}

- Tax compliance optimization

- Data synchronization efficiency improvement

- Business scenario adaptation

# Process Scope Design {#process-scope-design .LS_Heading-1}

1.  

## Business Process for Standard Customer Billing流程图 {#business-process-for-standard-customer-billing流程图 .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| Process Step | Process Step Description                                                                                               | Transaction/App               | Business Role  |
+==============+========================================================================================================================+===============================+================+
| 001          | HC_SAP_DD_SD03_003.01_Delivery Processing                                                                              | N/A                           | Planner        |
|              |                                                                                                                        |                               |                |
|              | \* When planners have finished the Delivery Process and PGI in the system, they can continue with the billing process. |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 002          | Update PGI in the SAP system.                                                                                          | VL02N                         | Planner        |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 003          | The SAP system will auto generate the customer billing documents without any accounting document.                      | N/A                           | AR Admin       |
|              |                                                                                                                        |                               |                |
|              | \* customer billing email will be triggered.                                                                           |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 0031         | Upload shipping document into Billing document                                                                         | VF02N/Manage Billing Document | Logistics Team |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 004          | The SAP system will auto run a daily check to decide if the billing has met the requirements to release to accounting. | N/A                           | AR Admin       |
|              |                                                                                                                        |                               |                |
|              | \* All billing documents created after 5pm will be taken into account in the next day.                                 |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 005          | The SAP system will decide if a billing document is to be released or not.                                             | N/A                           | AR Admin       |
|              |                                                                                                                        |                               |                |
|              | - If yes, proceed to step 006                                                                                          |                               |                |
|              |                                                                                                                        |                               |                |
|              | If no, proceed to step 007                                                                                             |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 006          | The SAP system will auto release the billing to accounting.                                                            | N/A                           | AR Admin       |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 007          | The SAP system will postpone the schedule and check the billing documents again the following day.                     | N/A                           | Planner        |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
|              |                                                                                                                        |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| **流程步骤​​** | **​​流程说明**                                                                                                           | **​​事务代码/应用​​**             | **​​业务角色​​**   |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 001          | HC_SAP_DD_SD03_003.01_交付处理\                                                                                        | N/A                           | Planner        |
|              | 当计划员在系统中完成交付流程和过账发货（PGI）后，可继续进行开票流程。\                                                 |                               |                |
|              | 在 SAP 系统中更新过账发货信息。\                                                                                       |                               |                |
|              | SAP 系统将自动生成客户开票凭证，且不生成任何会计凭证。                                                                 |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 002          | 在 SAP 系统中更新过账发货信息。                                                                                        | VL02N                         | Planner        |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 003          | SAP 系统将自动生成客户开票凭证，且不生成任何会计凭证。\                                                                | N/A                           | AR Admin       |
|              | 系统将触发客户开票邮件。                                                                                               |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 0031         | 上传发货附件到开票凭证中                                                                                               | VF02N/Manage Billing Document | AR Admin       |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 004          | SAP 系统将每日自动检查，判断开票是否满足释放至会计模块的要求。                                                         | N/A                           | Logistics Team |
|              |                                                                                                                        |                               |                |
|              | 所有在下午 5 点后创建的开票凭证将计入次日。                                                                            |                               |                |
|              |                                                                                                                        |                               |                |
|              | SAP 系统将判断是否释放该开票凭证。                                                                                     |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 005          | SAP 系统将判断是否释放该开票凭证。                                                                                     | N/A                           | AR Admin       |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 006          | 若满足，进入步骤 006\                                                                                                  | N/A                           | AR Admin       |
|              | SAP 系统将自动将开票过账至会计模块。                                                                                   |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
| 007          | 若不满足，进入步骤 007                                                                                                 | N/A                           | Planner        |
|              |                                                                                                                        |                               |                |
|              | SAP 系统将推迟计划，并在次日重新检查该开票凭证。                                                                       |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
|              |                                                                                                                        |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
|              |                                                                                                                        |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+
|              |                                                                                                                        |                               |                |
+--------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------+----------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- Billing Documents need creating and releasing automatically.

- Billing Date = PGI Date+ Route Date

- Email Form to Planner

- Save to Sharepoint(Via Interface---To check if ok or not)\--TBD

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

## Billing Dcoument {#billing-dcoument .LS_Heading-3}

  ------------------------------------------------------------------------------------------
   **Document Type**  **Description**                        **Comments**
  ------------------- -------------------------------------- -------------------------------
          F2          Delivery-related invoice               

          G2          Credit memo                            

          L2          Debit memo                             

         CBRE         Credit memo for returns                

          S1          Cancellation invoice                   

          S2          Cancellation credit memo               

          FAZ         Down payment request                   

          FAS         Cancellation of Down payment request   

          IV          Inter Company Billing                  

     **​​文档类型​​**     **​​描述​​**                               **​​注释​​**

          F2          发票                                   

          G2          贷项凭证                               

          L2          借项凭证                               

         CBRE         退货贷项凭证                           

          S1          发票作废                               

          S2          贷项凭证取消                           

          FAZ         预付款请求                             

          FAS         预付款申请取消                         

          IV          公司间开票                             
  ------------------------------------------------------------------------------------------

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Link to Golden Tax system

# Process Scope Design {#process-scope-design-1 .LS_Heading-1}

2.  

## Business Process for Intercompany Billing 流程图 {#business-process-for-intercompany-billing-流程图 .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| Process Step | Process Step Description                                                                                                                                                  | Transaction/App     | Business Role  |
+==============+===========================================================================================================================================================================+=====================+================+
| 001          | HC_SAP_DD_SD03_003.01_Delivery Processing                                                                                                                                 | N/A                 | Planner        |
|              |                                                                                                                                                                           |                     |                |
|              | \* When planners have finished the Delivery Process and PGI in the system, they can continue with the billing process.                                                    |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 002          | Update PGI in the SAP system.                                                                                                                                             | VL02N               | Planner        |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 003          | The SAP system will auto generate the customer billing documents without any accounting document.                                                                         | N/A                 | AR Admin       |
|              |                                                                                                                                                                           |                     |                |
|              | \* customer billing email will be triggered.                                                                                                                              |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 0031         | Upload shipping document into Billing document                                                                                                                            | N/A                 | Logistics Team |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 004          | The SAP system will auto run a daily check to decide if the billing has met the requirements to release to accounting.                                                    | N/A                 | AR Admin       |
|              |                                                                                                                                                                           |                     |                |
|              | \* All billing documents created after 5pm will be taken into account in the next day.                                                                                    |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 005          | The SAP system will decide if a billing document is to be released or not.                                                                                                | N/A                 | AR Admin       |
|              |                                                                                                                                                                           |                     |                |
|              | - If yes, proceed to step 006                                                                                                                                             |                     |                |
|              |                                                                                                                                                                           |                     |                |
|              | If no, proceed to step 007                                                                                                                                                |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 006          | The SAP system will auto release the billing to accounting.                                                                                                               | N/A                 | SAP System     |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 007          | The SAP system will postpone the schedule and check the billing documents again the following day.                                                                        | N/A                 | AR Admin       |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 008          | Reference drop shipment delivery note to create inter-company billing,1 step to create billing and release billing accounting, automatically processed by background job. | N/A                 | AR Admin       |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 009          | Reference drop shipment delivery note to create inter-company billing,1 step to create billing and release billing accounting, automatically processed by background job. | N/A                 | AR Admin       |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
|              |                                                                                                                                                                           |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| **流程步骤​​** | **​​流程说明**                                                                                                                                                              | **​​事务代码/应用​​**   | **​​业务角色​​**   |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 001          | HC_SAP_DD_SD03_003.01_交付处理\                                                                                                                                           | N/A                 | Planner        |
|              | 当计划员在系统中完成交付流程和过账发货（PGI）后，可继续进行开票流程。\                                                                                                    |                     |                |
|              | 在 SAP 系统中更新过账发货信息。\                                                                                                                                          |                     |                |
|              | SAP 系统将自动生成客户开票凭证，且不生成任何会计凭证。                                                                                                                    |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 002          | 在 SAP 系统中更新过账发货信息。                                                                                                                                           | VL02N               | Planner        |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 003          | SAP 系统将自动生成客户开票凭证，且不生成任何会计凭证。\                                                                                                                   | N/A                 | AR Admin       |
|              | 系统将触发客户开票邮件。                                                                                                                                                  |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 0031         | 上传发货附件到开票凭证中                                                                                                                                                  | N/A                 | Logistics Team |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 004          | SAP 系统将每日自动检查，判断开票是否满足释放至会计模块的要求。                                                                                                            | N/A                 | AR Admin       |
|              |                                                                                                                                                                           |                     |                |
|              | 所有在下午 5 点后创建的开票凭证将计入次日。                                                                                                                               |                     |                |
|              |                                                                                                                                                                           |                     |                |
|              | SAP 系统将判断是否释放该开票凭证。                                                                                                                                        |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 005          | SAP 系统将判断是否释放该开票凭证。                                                                                                                                        | N/A                 | AR Admin       |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 006          | 若满足，进入步骤 006\                                                                                                                                                     | N/A                 | SAP System     |
|              | SAP 系统将自动将开票过账至会计模块。                                                                                                                                      |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 007          | 若不满足，进入步骤 007                                                                                                                                                    | N/A                 | AR Admin       |
|              |                                                                                                                                                                           |                     |                |
|              | SAP 系统将推迟计划，并在次日重新检查该开票凭证。                                                                                                                          |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 008          | 参考直运交货单创建公司间开票，一步完成开票创建及开票会计凭证过账，由后台作业自动处理。                                                                                    | N/A                 | AR Admin       |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
| 009          | 参考直运交货单创建公司间开票，一步完成开票创建及开票会计凭证过账，由后台作业自动处理。                                                                                    | /A                  | AR Admin       |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+
|              |                                                                                                                                                                           |                     |                |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+----------------+

## HC Functional Requirements {#hc-functional-requirements-1 .LS_Heading-3}

- Billing Documents need creating and releasing automatically.

- Billing Date = PGI Date+ Route Date

- Email Form to Planner

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-1 .LS_Heading-3}

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- Standard POs (NB Doc Type) will be used for direct materials purchases.

- Default document number ranges will be used for Purchase orders.

- PR/PO release strategies and workflows will be set up to support approvals as defined in section 3.4.

- Custom field is required to select PR/PO Text-Id.

- All inventory materials will have both purchasing and MRP views.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-1 .LS_Heading-3}

- Procurement of direct materials is tightly integrated with other business processes, such as:

  - Materials forecasting and planning.

  - Inventory and warehouse management.

  - Quality management

  - Accounting

- General ledger postings resulting from goods receipts, returns, and invoice postings will be configured in financial accounting.

- ​**​**

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-2 .LS_Heading-1}

3.  

## Business Process for Credit/Debit Memo 流程图 {#business-process-for-creditdebit-memo-流程图 .LS_Heading-3}

![](media/media/image4.emf)

## Stnadard Business Process Steps {#stnadard-business-process-steps .LS_Heading-3}

+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| Process Step | Process Step Description                                                     | Transaction/App   | Business Role      |
+==============+==============================================================================+===================+====================+
| 001          | Received Credit/ Debit Memo Request                                          | N/A               | Requester          |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 002          | Create Credit/ Debit Memo Sales Order in the SAP System                      | VA01              | Requester          |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 003          | Input Price with PPR0 and Save                                               | N/A               | Requester          |
|              |                                                                              |                   |                    |
|              | \* With FG real Material on Item                                             |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 004          | AR Admin Approved?                                                           | N/A               | AR Admin           |
|              |                                                                              |                   |                    |
|              | If not approved, go to step 008                                              |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 005          | If approved, go to step 005                                                  | VA01              | AR Admin           |
|              |                                                                              |                   |                    |
|              | Department Manager approved, go to step 006                                  |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 006          | If Department Manager approved, go to Step 007                               | N/A               | Department Manager |
|              |                                                                              |                   |                    |
|              | If not approved, go to step 008                                              |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 007          | If Department Manager approved, go to step 007                               | VF01              | AR Admin           |
|              |                                                                              |                   |                    |
|              | Create Credit/ Debit Memo                                                    |                   |                    |
|              |                                                                              |                   |                    |
|              | \* Credit Memo/Debit Memo email will be triggered to AR Admin and Requester. |                   |                    |
|              |                                                                              |                   |                    |
|              | If not approved, go to step 008                                              |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
|              |                                                                              |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| **流程步骤​​** | **​​流程说明**                                                                 | **​​事务代码/应用​​** | **​​业务角色​​**       |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 001          | 接收到贷项 / 借项通知单请求                                                  | N/A               | Requester          |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 002          | 在 SAP 系统中创建贷项 / 借项凭证申请销售订单                                 | VA01              | Requester          |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 003          | 输入PPR0价格并保存                                                           | N/A               | Requester          |
|              |                                                                              |                   |                    |
|              | \*项目中包含产成品实际物料                                                   |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 004          | 应收账款管理员已批准？                                                       | N/A               | AR Admin           |
|              |                                                                              |                   |                    |
|              | 若未批准，进入步骤 008                                                       |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 005          | 部门经理已批准？                                                             | VA01              | Department Manager |
|              |                                                                              |                   |                    |
|              | 若已批准，进入步骤 006                                                       |                   |                    |
|              |                                                                              |                   |                    |
|              | 若未批准，进入步骤008                                                        |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 006          | 财务经理已批准？                                                             | N/A               | Finance Manager    |
|              |                                                                              |                   |                    |
|              | 若已批准，进入步骤 007                                                       |                   |                    |
|              |                                                                              |                   |                    |
|              | 若未批准，进入步骤 008                                                       |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
| 007          | 若已批准，进入步骤 007                                                       | VF01              | AR Admin           |
|              |                                                                              |                   |                    |
|              | 创建贷项 / 借项凭证                                                          |                   |                    |
|              |                                                                              |                   |                    |
|              | 系统将触发贷项凭证 / 借项凭证邮件发送给AR admin 和Requester。                |                   |                    |
|              |                                                                              |                   |                    |
|              | 若未批准，进入步骤 008                                                       |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+
|              |                                                                              |                   |                    |
+--------------+------------------------------------------------------------------------------+-------------------+--------------------+

## HC Functional Requirements {#hc-functional-requirements-2 .LS_Heading-3}

- Require Approval

- Approval levels should include AR Admin 、Department Manager 、Finance Manager

## HC Delegation Of Authority {#hc-delegation-of-authority-2 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-2 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-2 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-2 .LS_Heading-3}

- ​**​**N/A

## Support / Closing Considerations {#support-closing-considerations-1 .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-3 .LS_Heading-1}

4.  

## Business Process for GTS 流程图 {#business-process-for-gts-流程图 .LS_Heading-3}

![](media/media/image5.emf)

![](media/media/image6.emf)

## GTS Business Process Steps {#gts-business-process-steps .LS_Heading-3}

+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| Process Step | Process Step Description                                                    | Transaction/App   | Business Role |
+==============+=============================================================================+===================+===============+
| 001          | Link to Process HC_SAP_DD_SD04-01-Standard Billing Proccess                 |                   | AR Admin      |
|              |                                                                             |                   |               |
|              | After Billing Documents were created in SAP , go to step 002.               |                   |               |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| 002          | Before creating the invoice ,AR Admin may need to login GTS first via 诺诺. |                   | AR Admin      |
|              |                                                                             |                   |               |
|              | AR Admin Create Golden Tax Invoice in SAP.                                  |                   |               |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| 003          | Golden Tax Invoice will be created automatically in GTS                     | GTS               | AR Admin      |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| 004          | The VAT Number will be updated automatically back to Billing document       | VF02              | SAP           |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
|              |                                                                             |                   |               |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                                | **​​事务代码/应用​​** | **​​业务角色​​**  |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| 001          | 衔接 SAP 开票流程。                                                         |                   | AR Admin      |
|              |                                                                             |                   |               |
|              | SAP 自动开完发票后，进入步骤002。                                           |                   |               |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| 002          | 创建发票之前，AR Admin 需登录诺诺网。                                       |                   | AR Admin      |
|              |                                                                             |                   |               |
|              | 然后在SAP 中创建金税发票。                                                  |                   |               |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| 003          | 在金税系统中自动创建金税发票                                                | GTS               | AR Admin      |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
| 004          | 金税发票号会自动反写回系统标准的发票的抬头                                  | VF02/更改开票凭证 | SAP           |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+
|              |                                                                             |                   |               |
+--------------+-----------------------------------------------------------------------------+-------------------+---------------+

## Cancel GTS Business Process Steps {#cancel-gts-business-process-steps .LS_Heading-3}

+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| Process Step | Process Step Description                                                                            | Transaction/App               | Business Role |
+==============+=====================================================================================================+===============================+===============+
| 001          | Link to Process                                                                                     | N/A                           | AR Admin      |
|              |                                                                                                     |                               |               |
|              | HC_SAP_DD_SD04 -04-01- Golden Tax System Billing Processing                                         |                               |               |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 002          | Cancel Billing Document                                                                             | VF02/ Manage Billing Doument  | AR Admin      |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 003          | The cancel Billing Document Number will be written to the Create Golden tax invoice page.           |                               | SAP           |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 004          | AR Admin need to login nuonuo first.                                                                | Golden tax request            | AR Admin      |
|              |                                                                                                     |                               |               |
|              | Select one billing nubmer and cancel.                                                               |                               |               |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 005          | The Goldex Tax Invoice will be created automatically in GTS                                         | GTS                           | AR Admin      |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 006          | Print the VAT Invoice                                                                               | Golden tax request            | AR Admin      |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 007          | The Cancellation VAT Number will be updated automatically back to the Cancellation Billing document | VF02                          | SAP           |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
|              |                                                                                                     |                               |               |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                                                        | **​​事务代码/应用​​**             | **​​业务角色​​**  |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 001          | 创建开票凭证                                                                                        | VF01创建开票凭证/管理开票凭证 | AR Admin      |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 002          | 在开票凭证中上传扫描的交货单相关附件                                                                | VF02/ 管理开票凭证            | AR Admin      |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 003          | 取消之前，AR Admin需要登录诺诺网。                                                                  | Golden tax request            | AR Admin      |
|              |                                                                                                     |                               |               |
|              | 选中需要取消的金税发票号，先取消SAP 的发票号，再取消金税发票。                                      |                               |               |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 004          | 在金税APP中打印取消的VAT发票                                                                        | GTS                           | AR Admin      |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
| 005          | 金税发票号会自动反写回系统标准的取消类型的发票的抬头                                                | VF02更改开票凭证              | SAP           |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+
|              |                                                                                                     |                               |               |
+--------------+-----------------------------------------------------------------------------------------------------+-------------------------------+---------------+

## HC Functional Requirements {#hc-functional-requirements-3 .LS_Heading-3}

- Need a Remark field for Some Remarks get from Invoice.

This Remark field(TBD) needs editable. This function needs further communication. This Remark field needs to contain these information(Billing Number , Customer PO ,Customer Material)

- How to handle with the difference in SAP Billing with GTS Billing.(TBD)

## HC Delegation Of Authority {#hc-delegation-of-authority-3 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-3 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-3 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-3 .LS_Heading-3}

- ​**​**N/A

## Support / Closing Considerations {#support-closing-considerations-2 .LS_Heading-3}

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

## rization Roles {#rization-roles .LS_Heading-3}

+-------------------+-------------------------------------------------------------------------------+--------------------------------+---------------------------------+
| **Business Role** | **Role Description**                                                          | **Authorization Restrictions** | **Baseline ZRS Role(s)**        |
+===================+===============================================================================+================================+=================================+
| **Planner**       | **Create delivery,PGI**                                                       | VL01N,                         | Z_Planner_CN                    |
|                   |                                                                               |                                |                                 |
|                   |                                                                               | VL02N,                         |                                 |
|                   |                                                                               |                                |                                 |
|                   |                                                                               | VL03N                          |                                 |
|                   |                                                                               |                                |                                 |
|                   |                                                                               | Manage Outbound Delivery       |                                 |
+-------------------+-------------------------------------------------------------------------------+--------------------------------+---------------------------------+
| **AR Admin**      | Create a Credit Memo/Debit Meme request                                       | VA01                           | Z_AR_Admin_CN                   |
|                   |                                                                               |                                |                                 |
|                   | Create, Change & Display Billing Document (Invoice, Credit Memo & Debit Memo) | VA02                           |                                 |
|                   |                                                                               |                                |                                 |
|                   | Create the Outbound File for GTS Interface (China) from SAP                   | VF01, VF02, VF03               |                                 |
|                   |                                                                               |                                |                                 |
|                   | Upload the Inbound File from GTS Interface (China) to SAP                     | Manage Billing Document        |                                 |
|                   |                                                                               |                                |                                 |
|                   | Cancel Billing Document                                                       |                                |                                 |
+-------------------+-------------------------------------------------------------------------------+--------------------------------+---------------------------------+
|                   |                                                                               |                                |                                 |
+-------------------+-------------------------------------------------------------------------------+--------------------------------+---------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------------------------------------------------------------------------
  F2                      OR (Standard Order) 🡺 LF (Delivery) 🡺 WL (material doc) 🡺 F2 (Invoice) 🡺 RV (Accounting doc)

  S2                      CR (Credit memo request) 🡺 G2 (Credit Memo) 🡺 RV (Accounting doc) 🡺 S2 (Can. Credit) 🡺 RV (Accounting doc)

  F5                      OR (Standard Order) 🡺 F5 (Pro forma)

  G2                      OR (Standard Order) 🡺 G2 (Credit Memo)

  L2                      OR (Standard Order) 🡺 L2 (Debit Memo)

  CBRE                    F2 (Invoice) 🡺 CR (Credit memo Request) 🡺 LR (Returns Delivery) 🡺 WL (material doc) 🡺 CBRE (Credit for Returns)

  FAZ                     OR (Standard Order) 🡺 FAZ (Down payment request)

  FAS                     OR (Standard Order) 🡺 FAZ (Down payment request) 🡺 FAS (Can. Down payment request)

  IV                      OR (Standard Order) 🡺 LF (Delivery) 🡺 WL (material doc) 🡺 F2 (Invoice) 🡺 IV (Intercompany billing)
  -----------------------------------------------------------------------------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **SAP App**                    | **Description / Usage**                                                                                                                                                                                                                                        |
+================================+================================================================================================================================================================================================================================================================+
| Sales Volume Flexible Analysis | You can use this app to gain an understanding of the monthly sales volume                                                                                                                                                                                      |
+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Sales Volume Check Open Sales  | With this app, you as a sales manager can check your sales volume in comparison with previous months, with the additional insight of open orders and open deliveries for the current month.                                                                    |
|                                |                                                                                                                                                                                                                                                                |
|                                | This enables you to see at a glance how the current month\'s sales volume relates to the previous month, and shows you where you can still increase your sales volume in the current period, for example, open orders, open billing requests, open deliveries. |
+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Sales Volume Open Sales by Org | With this app, you as a sales manager can check your sales volume in comparison with previous months, with the additional insight of open orders and open deliveries for the current month.                                                                    |
|                                |                                                                                                                                                                                                                                                                |
|                                | This enables you to see at a glance how the current month\'s sales volume relates to the previous month, and shows you where you can still increase your sales volume in the current period, for example, open orders, open billing requests, open deliveries. |
+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                |                                                                                                                                                                                                                                                                |
+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                |                                                                                                                                                                                                                                                                |
+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                                                          |
+-----------------+---------------------------------------------------------+----------------+------------------+----------------+---------------------+
| **Report Name** | **Description**                                         | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                 |                                                         |                |                  |                |                     |
|                 |                                                         |                | **SAP App/Rprt** |                |                     |
+:================+:========================================================+:===============+:=================+:===============+:====================+
| ZSD335          | Overview Billing documents\                             |                |                  |                |                     |
|                 | The delivery and billing data are counted in one report |                |                  |                |                     |
+-----------------+---------------------------------------------------------+----------------+------------------+----------------+---------------------+
|                 |                                                         |                |                  |                |                     |
+-----------------+---------------------------------------------------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+--------------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                         |
+------------------+------------------+------------------+------------------+----------------------------+
| **Interface**    | **Description**  | **In Scope**     | **Complexity**   | **Comments**               |
+==================+:=================+:=================+:=================+:===========================+
| Golden Tax Sytem |                  |                  |                  | This will be in SAP system |
+------------------+------------------+------------------+------------------+----------------------------+

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
|               |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|               |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|               |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                                                                                                                                              |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+------------------+------------------+-------------------------+
| **Enhancement**                                              | **Description**                                                                                | **Complexity**   | **In Scope**     | **Comments**            |
+==============================================================+================================================================================================+==================+==================+:========================+
| Billing date value                                           | Users need this billing date = PGI Date + route date                                           | L1               |                  |                         |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+------------------+------------------+-------------------------+
| Customized Form Email subject                                | logistics nubmer in Billing document form needs bringing to email subject while sending email. | L1               |                  | In APPS development     |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+------------------+------------------+-------------------------+
| Billing Document Email to Planner（SO creator,CR/DR creator) | Users need to email to the SO Creator                                                          | L1               |                  | Maybe custom logic      |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+------------------+------------------+-------------------------+
|                                                              |                                                                                                |                  |                  |                         |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+------------------+------------------+-------------------------+
|                                                              |                                                                                                |                  |                  |                         |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+------------------+------------------+-------------------------+
|                                                              |                                                                                                |                  |                  |                         |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+------------------+------------------+-------------------------+

## Forms {#forms .LS_Heading-3}

The following forms have been identified as in scope:

+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Forms**                                                                                                                                                                                                                                                                                       |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| **Form**             | **Description**                                                                                                                                                                                              | **Complexity**    | **In Scope**      | **Comments**      |
+======================+==============================================================================================================================================================================================================+===================+===================+===================+
| SD billing document\ | N/A                                                                                                                                                                                                          | L1                |                   | Adobe template    |
| EN version           |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| SD Credit Memo\      | N/A                                                                                                                                                                                                          | L1                |                   | Adobe template    |
| EN version           |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| SD Debit Memo\       | N/A                                                                                                                                                                                                          | L1                |                   | Adobe template    |
| EN version           |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| SD billing document\ | Both inventory and price are in the sub-items. However, when invoicing, HC\'s customers hope to print only the main item (with both price and quantity reflected in the main item) instead of the sub-items. | L1                |                   | Adobe template    |
| For Kitting\         |                                                                                                                                                                                                              |                   |                   |                   |
| EN version           | The system\'s standard template prints both the main item and sub-items, but the price and quantity of the main item are zero.                                                                               |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
|                      |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| **表单​​**             | **​​描述​​**                                                                                                                                                                                                     | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| 开票凭证             | N/A                                                                                                                                                                                                          | L1                |                   | Adobe 开发        |
|                      |                                                                                                                                                                                                              |                   |                   |                   |
| 英文版               |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| 贷项凭证             | N/A                                                                                                                                                                                                          | L1                |                   | Adobe 开发        |
|                      |                                                                                                                                                                                                              |                   |                   |                   |
| 英文版               |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| 借项凭证             | N/A                                                                                                                                                                                                          | L1                |                   | Adobe 开发        |
|                      |                                                                                                                                                                                                              |                   |                   |                   |
| 英文版               |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| 销售包的打印         | 库存和价格都在子项，但是开票的时候，HC 的客户希望 只打印主项目（把价格和数量都体现在主项目上），不打印子项目。                                                                                               | L1                |                   | Adobe 开发        |
|                      |                                                                                                                                                                                                              |                   |                   |                   |
| 英文版               | 系统标准模板是打印主项目和子项目，但是主项目的价格和数量是0                                                                                                                                                  |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
|                      |                                                                                                                                                                                                              |                   |                   |                   |
+----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+

## Workflows {#workflows .LS_Heading-3}

The following workflows have been identified as in scope:

以下工作流被纳入范围：

+-----------------------------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                                                 |
+----------------------+------------------------------------+-------------------+-------------------+-------------------+
| **Workflow**         | **Description**                    | **Complexity**    | **In Scope**      | **Comments**      |
+======================+====================================+===================+===================+===================+
| CR Approval Workflow | Std Workflow                       | L1                | Yes               |                   |
+----------------------+------------------------------------+-------------------+-------------------+-------------------+
| DR Approval Workflow | Approvers are maintained HR tables | L1                | Yes               |                   |
+----------------------+------------------------------------+-------------------+-------------------+-------------------+
| **​​灵活工作流​​**       | **​​描述​​**                           | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+----------------------+------------------------------------+-------------------+-------------------+-------------------+
| ​​CR审批工作流​​         | 标准工作流                         | L1                | 是                |                   |
+----------------------+------------------------------------+-------------------+-------------------+-------------------+
| ​​DR审批工作流​​         | 审批人信息维护于HR系统表中         | L1                | 是                |                   |
+----------------------+------------------------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

# ![](media/media/image7.png){width="6.003662510936133in" height="2.5246161417322837in"} {#section .LS_Heading-1}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
