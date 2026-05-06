**Master Data**

**主数据流程**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_SD01 Master Data**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

        Warner Yu                SD Lead                15/08/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [5](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [5](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [6](#design-document-approval-options)](#design-document-approval-options)

[2. CUSTOMER MASTER [6](#customer-master)](#customer-master)

[2.1 Purpose [6](#purpose)](#purpose)

[2.2 Business Reason [6](#business-reason)](#business-reason)

[3. PRICING MASTER [7](#pricing-master)](#pricing-master)

[3.1 Purpose [7](#purpose-1)](#purpose-1)

[3.2 Business Reason [7](#business-reason-1)](#business-reason-1)

[4. CREDIT MASTER [7](#credit-master)](#credit-master)

[4.1 Purpose [7](#purpose-2)](#purpose-2)

[4.2 Business Reason [7](#business-reason-2)](#business-reason-2)

[5. CUSTOMER MATERIAL MASTER [7](#customer-material-master)](#customer-material-master)

[5.1 Purpose [7](#purpose-3)](#purpose-3)

[5.2 Business Reason [8](#business-reason-3)](#business-reason-3)

[6. CUSTOMER MASTER Process Scope Design [8](#customer-master-process-scope-design)](#customer-master-process-scope-design)

[6.1 Business Process for CUSTOMER MASTER流程图 [8](#business-process-for-customer-master流程图)](#business-process-for-customer-master流程图)

[6.1.1 Business Process Steps [8](#business-process-steps)](#business-process-steps)

[6.2 HC Functional Requirements [11](#hc-functional-requirements)](#hc-functional-requirements)

[6.3 Standard Documents / Settings [11](#standard-documents-settings)](#standard-documents-settings)

[6.4 Design Considerations / Key Assumptions [12](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[6.5 Cross Functional Integration Dependencies [12](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[6.6 Support / Closing Considerations [12](#support-closing-considerations)](#support-closing-considerations)

[7. PRICING MASTER Process Scope Design [12](#pricing-master-process-scope-design)](#pricing-master-process-scope-design)

[7.1 Business Process for PRICING MASTER流程图 [12](#business-process-for-pricing-master流程图)](#business-process-for-pricing-master流程图)

[7.1.1 Business Process Steps [12](#business-process-steps-1)](#business-process-steps-1)

[7.2 HC Functional Requirements [15](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[7.3 HC Delegation Of Authority [15](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[7.4 Design Considerations / Key Assumptions [15](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[7.5 Cross Functional Integration Dependencies [15](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[7.6 Support / Closing Considerations [15](#support-closing-considerations-1)](#support-closing-considerations-1)

[8. CREDIT MASTER Process Scope Design [16](#credit-master-process-scope-design)](#credit-master-process-scope-design)

[8.1 Business Process for CREDIT MASTER流程图 [16](#business-process-for-credit-master流程图)](#business-process-for-credit-master流程图)

[8.1.1 Business Process Steps [16](#business-process-steps-2)](#business-process-steps-2)

[8.2 HC Functional Requirements [17](#hc-functional-requirements-2)](#hc-functional-requirements-2)

[8.3 HC Delegation Of Authority [17](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[8.4 Standard Documents / Settings [17](#standard-documents-settings-1)](#standard-documents-settings-1)

[8.5 Design Considerations / Key Assumptions [17](#design-considerations-key-assumptions-2)](#design-considerations-key-assumptions-2)

[8.6 Cross Functional Integration Dependencies [17](#cross-functional-integration-dependencies-2)](#cross-functional-integration-dependencies-2)

[8.7 Support / Closing Considerations [17](#support-closing-considerations-2)](#support-closing-considerations-2)

[9. CUSTOMER MATERIAL MASTER Process Scope Design [18](#customer-material-master-process-scope-design)](#customer-material-master-process-scope-design)

[9.1 Business Process for CUSTOMER MATERIAL MASTER流程图 [18](#business-process-for-customer-material-master流程图)](#business-process-for-customer-material-master流程图)

[9.1.1 Business Process Steps [18](#business-process-steps-3)](#business-process-steps-3)

[9.2 HC Functional Requirements [20](#hc-functional-requirements-3)](#hc-functional-requirements-3)

[9.3 HC Delegation Of Authority [20](#hc-delegation-of-authority-2)](#hc-delegation-of-authority-2)

[9.4 Standard Documents / Settings [20](#standard-documents-settings-2)](#standard-documents-settings-2)

[9.5 Design Considerations / Key Assumptions [21](#design-considerations-key-assumptions-3)](#design-considerations-key-assumptions-3)

[9.6 1Cross Functional Integration Dependencies [21](#cross-functional-integration-dependencies-3)](#cross-functional-integration-dependencies-3)

[9.7 Support / Closing Considerations [21](#support-closing-considerations-3)](#support-closing-considerations-3)

[10. Authorization Roles [22](#authorization-roles)](#authorization-roles)

[10.1 Authorization Roles [22](#authorization-roles-1)](#authorization-roles-1)

[11. Document Types and Document Flow [23](#document-types-and-document-flow)](#document-types-and-document-flow)

[12. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [23](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[12.1 Reports [23](#reports)](#reports)

[12.1.1 Standard Reports [23](#standard-reports)](#standard-reports)

[12.1.2 HC Requested Reports [23](#hc-requested-reports)](#hc-requested-reports)

[12.2 Interfaces [23](#interfaces)](#interfaces)

[12.3 Conversions [24](#conversions)](#conversions)

[12.4 Enhancements [24](#enhancements)](#enhancements)

[12.5 Forms [24](#forms)](#forms)

[12.6 Workflows [25](#workflows)](#workflows)

[13. Legend for Process Flow [26](#legend-for-process-flow)](#legend-for-process-flow)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       25/07/2025

       2.0                 Changes after reviewing                 15/08/2025

                                                              
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

# CUSTOMER MASTER {#customer-master .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

A customer is a business partner to which goods and services are sold and delivered. A business partner can be a customer and a supplier at the same time if, for example, your customer also supplies goods to you.

A customer master holds information about the customer such as their name, address, bank details, tax details and delivery and billing preferences. This customer information is used and stored in transactions such as sales orders, deliveries and invoices.

Some customer information is specific to a particular company (known as company code) or sales unit (known as sales area) within your organization.

## Business Reason {#business-reason .LS_Heading-3}

In Home Control, planners will be responsible for collecting basic customer information, and finance for adding on the finance-related information. A central master data team will be assigned for SD Customer master creation to standardize the master data maintenance process.

\* El Paso should have a separate access of creating the master data for US business.

# PRICING MASTER {#pricing-master .LS_Heading-1}

3.  

<!-- -->

2.  

## Purpose {#purpose-1 .LS_Heading-3}

Sales pricing conditions are used to store the information required to undertake automatic pricing in a sales order. They include prices, discounts, surcharges and taxes. They may be specific to a particular customer or material or a combination of parameters.

A sales pricing condition holds information such as a price in a specific currency for a material or a customer specific discount as a percentage. This information is used and stored in the sales order and in billing documents such as invoices.

The information is generally specific to a particular sales unit within your organization.

## Business Reason {#business-reason-1 .LS_Heading-3}

In Home Control, the pricing conditions will be maintained according to the PPIA (Pricing Agreement) in the form of master data. Finance has the access authorization to maintain, change and de-activate the pricing master data upon the request of the account managers.

# CREDIT MASTER {#credit-master .LS_Heading-1}

4.  

<!-- -->

3.  

## Purpose {#purpose-2 .LS_Heading-3}

The credit worthiness and payment behavior of your business partners has an immediate effect on the business results of your company. Efficient receivables and credit management reduces the risk of financial losses and helps you to optimize business relationships with your business partners. Basic Credit Management supports your company in the early determination of the risk of losses on receivables from your business partners and supports you in making credit decisions. Basic Credit Management checks the exposure against the current credit limit for the business partner. In addition, you can also perform other checks, such as oldest open item, maximum dunning level, or last payment. If the new order is blocked, the blocked order can be released or rejected by authorized staff.

## Business Reason {#business-reason-2 .LS_Heading-3}

The credit-relevant business partner data is for monitoring credit risks. In Home Control, finance will be responsible to maintain the customer credit master.

# CUSTOMER MATERIAL MASTER {#customer-material-master .LS_Heading-1}

5.  

<!-- -->

4.  

## Purpose {#purpose-3 .LS_Heading-3}

In SAP, Customer Material refers to the specific number or description assigned by a customer to the materials they purchase or use. Customer material information can be associated with the supplier\'s material number in the SAP system to ensure that these materials can be accurately identified and processed during order handling, shipment, and billing. The main purposes of customer materials include simplifying order processing, improving shipment accuracy, and enhancing customer service.

## Business Reason {#business-reason-3 .LS_Heading-3}

In Home Control, planners will be responsible for the customer material maintenance. Customer material is created when customers provide their material information like part number.

# Free Goods Rate {#free-goods-rate .LS_Heading-1}

6.  

<!-- -->

5.  

## Purpose {#purpose-4 .LS_Heading-3}

To simplify the process of Free goods.

## Business Reason {#business-reason-4 .LS_Heading-3}

In Home Control, sometimes customers request the free goods

# CUSTOMER MASTER Process Scope Design {#customer-master-process-scope-design .LS_Heading-1}

1.  

## Business Process for CUSTOMER MASTER流程图 {#business-process-for-customer-master流程图 .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| Process Step | Process Step Description                                                                                                                                                                            | Business Role        | Transaction/App                  |
+==============+=====================================================================================================================================================================================================+======================+==================================+
| 1.           | Provide customer basic information to Finance to search.                                                                                                                                            | **Planner**          | **N/A**                          |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | ***\* The information may include company name, address, etc.***                                                                                                                                    |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 2.           | Search the customer master in the SAP system                                                                                                                                                        | **AR Admin**         | **Manage Customer Master Data/** |
|              |                                                                                                                                                                                                     |                      |                                  |
|              |                                                                                                                                                                                                     |                      | **Maintain Business Partner**    |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 3.           | Decide if that customer master has existed already. This is to avoid any duplicate creation of customers in the SAP system.                                                                         | **AR Admin**         | **N/A**                          |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - If yes, proceed to step 004                                                                                                                                                                       |                      |                                  |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - If no, proceed to step 005                                                                                                                                                                        |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 4.           | Decide if there is any data change required                                                                                                                                                         | **AR Admin**         | **N/A**                          |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - If yes, proceed to step 015                                                                                                                                                                       |                      |                                  |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - If no, proceed to step 012                                                                                                                                                                        |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 5.           | If no existing customer master has been found in the SAP system, notify the planner that this is a new customer and more customer-related information is required for the customer master creation. | **AR Admin**         | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 6.           | Fill in the complete information about the customer in the application form and apply department manager's approval and then send to Finance via email.                                             | **Planner**          | **N/A**                          |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | ***\* This should include the Customer Name, Address, Contact information etc.***                                                                                                                   |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 7.           | Add on the finance-related inputs in the application form.                                                                                                                                          | **AR Admin**         | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 8.           | Send the application form to Finance Manager for approval.                                                                                                                                          | **AR Admin**         | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 9.           | **Finance manager decides if the request can be approved.**                                                                                                                                         | **Finance Manager**  | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 10.          | Create or update the customer master                                                                                                                                                                | **Master Data Team** | **Manage Customer Master Data/** |
|              |                                                                                                                                                                                                     |                      |                                  |
|              |                                                                                                                                                                                                     |                      | **Maintain Business Partner**    |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 11.          | Inform the planner about the successful/ unsuccessful creation/ update completion status. Inform the Planner on the customer number created in the SAP system via email.                            | **Master Data Team** | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 12.          | If the data has existed in the SAP system and there is no data to be changed, notify the planners that the customer has existed and no action is required.                                          | **AR Admin**         | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 13.          | If the Finance Manager doesn't approve the customer master creation request, AR admin will inform the planners that the creation request is not successful.                                         | **AR Admin**         | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 14.          | Planners will facilitate and arrange the discussions between Finance Manager and Key Account Manager to settle down the customer creation issue.                                                    | **Planner**          | **N/A**                          |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | *\* After the issue got resolved, planners will re-submit the application form and proceed to step 006*                                                                                             |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 15.          | If the data has existed in the SAP system and data needs to be changed, planner can directly update this existing customer master.                                                                  | **Master Data Team** | **Manage Customer Master Data/** |
|              |                                                                                                                                                                                                     |                      |                                  |
|              |                                                                                                                                                                                                     |                      | **Maintain Business Partner**    |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
|              |                                                                                                                                                                                                     |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| **流程**     | **​​流程步骤说明**                                                                                                                                                                                    | **​​业务角色​​**         | **事务代码/应用​​**                |
|              |                                                                                                                                                                                                     |                      |                                  |
| **步骤​​**     |                                                                                                                                                                                                     |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 1.           | > 向财务部门提供客户基本信息以供查询                                                                                                                                                                | 计划员               | **N/A**                          |
|              | >                                                                                                                                                                                                   |                      |                                  |
|              | > 信息可能包括公司名称、地址等                                                                                                                                                                      |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 2.           | > 在 SAP 系统中查询客户主数据                                                                                                                                                                       | 应收账款管理员       | 管理客户主数据/维护业务伙伴      |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 3.           | > 判断该客户主数据是否已存在。此举是为了避免在 SAP 系统中重复创建客户                                                                                                                               | 应收账款管理员       | **N/A**                          |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - 若是，进入步骤 004                                                                                                                                                                                |                      |                                  |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - 若否，进入步骤 005                                                                                                                                                                                |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 4.           | > 判断是否需要更改数据                                                                                                                                                                              | 应收账款管理员       | **N/A**                          |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - 若是，进入步骤 015                                                                                                                                                                                |                      |                                  |
|              |                                                                                                                                                                                                     |                      |                                  |
|              | - 若否，进入步骤 012                                                                                                                                                                                |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 5.           | > 若在 SAP 系统中未找到现有客户主数据，通知计划员该客户为新客户，创建客户主数据需要更多与客户相关的信息。                                                                                           | 应收账款管理员       | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 6.           | > 在申请表中填写客户的完整信息，部门经理审批通过后邮件发送给财务部门。                                                                                                                              | 计划员               | **N/A**                          |
|              | >                                                                                                                                                                                                   |                      |                                  |
|              | > 信息应包括客户名称、地址、联系方式等。                                                                                                                                                            |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 7.           | > 在申请表中补充财务相关信息。                                                                                                                                                                      | 应收账款管理员       | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 8.           | > 将申请表发送给财务经理审批。                                                                                                                                                                      | 应收账款管理员       | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 9.           | > 财务经理判断该请求是否可批准。                                                                                                                                                                    | 财务经理             | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 10.          | > 创建或更新客户主数据                                                                                                                                                                              | 主数据团队           | 管理客户主数据/维护业务伙伴      |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 11.          | > 通知计划员创建 / 更新是否成功完成。通过邮件告知计划员在 SAP 系统中创建的客户编号                                                                                                                  | 主数据团队           | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 12.          | > 若 SAP 系统中已存在该数据且无需更改，则通知计划员该客户已存在且无需采取行动。                                                                                                                     | 应收账款管理员       | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 13.          | > 若财务经理未批准客户主数据创建请求，应收账款管理员将通知计划员该创建请求未成功。                                                                                                                  | 应收账款管理员       | **N/A**                          |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 14.          | > 计划员将协助并安排财务经理与大客户经理之间的讨论，以解决客户创建问题。                                                                                                                            | 计划员               | **N/A**                          |
|              | >                                                                                                                                                                                                   |                      |                                  |
|              | > 问题解决后，计划员将重新提交申请表并进入步骤 006。                                                                                                                                                |                      |                                  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+
| 15.          | > 若 SAP 系统中已存在该数据且需要更改，计划员可直接更新该现有客户主数据。                                                                                                                           | 主数据团队           | 管理客户主数据/维护业务伙伴      |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------+----------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# PRICING MASTER Process Scope Design {#pricing-master-process-scope-design .LS_Heading-1}

2.  

## Business Process for PRICING MASTER流程图 {#business-process-for-pricing-master流程图 .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| Process Step | Process Step Description                                                                                                                             | Business Role       | Transaction/App               |
+==============+======================================================================================================================================================+=====================+===============================+
| **001**      | Finalize the negotiation on the quotation with customers. The Account Manager will submit the quotation to the customer and finalize the price.      | **Account Manager** | **N/A**                       |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **002**      | Once the price is finalized with the customer, account managers will raise up a request for pricing condition creation and send the PPIA to planner. | **Account Manager** | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | *\* PPIA will act as a basis for updating price in the SAP system.*                                                                                  |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **003**      | Based on the PPIA, search the pricing master in the SAP system.                                                                                      | **AR Admin**        | **VK13/Manage Prices -Sales** |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **004**      | Search the pricing conditions and decide if the pricing master has existed already                                                                   | **AR Admin**        | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | - If yes, proceed to step 005.                                                                                                                       |                     |                               |
|              |                                                                                                                                                      |                     |                               |
|              | - If no, proceed to step 006.                                                                                                                        |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **005**      | Based on this search, decide if there is a data change required.                                                                                     | **AR Admin**        | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | - If yes, proceed to step 006.                                                                                                                       |                     |                               |
|              |                                                                                                                                                      |                     |                               |
|              | - If no, end                                                                                                                                         |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **006**      | Inform Finance to create a new pricing master if no existing pricing master has been found in the SAP system                                         | **AR Admin**        | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | Inform Finance to update an existing pricing master if the data has existed in the SAP system and there is a data change requirement                 |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **007**      | Based on the information provided by the Planner, create or update the pricing master in the SAP system.                                             | **AR Admin**        | **VK13/Manage Prices -Sales** |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **008**      | Judge if approved or not.                                                                                                                            | **Finance Manager** | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | If not approved, go back t Step 007,                                                                                                                 |                     |                               |
|              |                                                                                                                                                      |                     |                               |
|              | If approved, go back t Step 009                                                                                                                      |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **009**      | Inform the planner about the successful/ unsuccessful creation/ update completion status                                                             | **AR Admin**        | **N/A**                       |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **010**      | File the PPIA for future reference                                                                                                                   | **AR Admin**        | **N/A**                       |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
|              |                                                                                                                                                      |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **流程步骤​​** | **​​流程步骤​​​​**                                                                                                                                         | **​​业务角色**        | **​​事务代码/应用**             |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **001**      | > 完成与客户的报价谈判。客户经理将向客户提交报价并确定价格。                                                                                         | 客户经理            | **N/A**                       |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **002**      | > 一旦与客户确定价格，客户经理将提出定价条件创建请求，并将 PPIA 发送给计划员。                                                                       | 客户经理            | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | - PPIA 将作为在 SAP 系统中更新价格的依据。                                                                                                           |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **003**      | > 根据 PPIA，在 SAP 系统中搜索定价主数据。                                                                                                           | 计划员              | VK13/管理价格-销售            |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **004**      | > 搜索定价条件并判断定价主数据是否已存在                                                                                                             | 计划员              | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | - 若是，进入步骤 005。                                                                                                                               |                     |                               |
|              |                                                                                                                                                      |                     |                               |
|              | - 若否，进入步骤 006。                                                                                                                               |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **005**      | > 根据搜索结果，判断是否需要更改数据。                                                                                                               | 计划员              | **N/A**                       |
|              |                                                                                                                                                      |                     |                               |
|              | - 若是，进入步骤 006。                                                                                                                               |                     |                               |
|              |                                                                                                                                                      |                     |                               |
|              | - 若否，流程结束                                                                                                                                     |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **006**      | > 若在 SAP 系统中未找到现有定价主数据，通知财务创建新的定价主数据；                                                                                  | 计划员              | **N/A**                       |
|              | >                                                                                                                                                    |                     |                               |
|              | > 若 SAP 系统中存在数据且需要更改，通知财务更新现有定价主数据                                                                                        |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **007**      | > 根据计划员提供的信息，在 SAP 系统中创建或更新定价主数据。                                                                                          | 应收账款管理员      | VK13/管理价格-销售            |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **008**      | > 判断是否审批。                                                                                                                                     | 财务经理            | **N/A**                       |
|              | >                                                                                                                                                    |                     |                               |
|              | > 如果审批通过，进入步骤009，                                                                                                                        |                     |                               |
|              | >                                                                                                                                                    |                     |                               |
|              | > 如果审批不通过，返回步骤007.                                                                                                                       |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **009**      | > 通知计划员创建 / 更新是否成功完成                                                                                                                  | 应收账款管理员      | **N/A**                       |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
| **010**      | > 将 PPIA 归档以备将来参考                                                                                                                           | 应收账款管理员      | **N/A**                       |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+
|              |                                                                                                                                                      |                     |                               |
+--------------+------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+-------------------------------+

## HC Functional Requirements {#hc-functional-requirements-1 .LS_Heading-3}

- Need approval

- Need to use sales scale(Not sap standard scale,need customizing-Different sales volume with different price for each customer )

- Need to upload attachment（Not support in ES）.Users will upload files in sharepoint

- Jane Chen need a new manual Price Type to enter the price

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- Approval: Every condition record needs finance manager's approval.

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-1 .LS_Heading-3}

- Jean Ong needs the change report , but the priority is low(in next phase).

## Support / Closing Considerations {#support-closing-considerations-1 .LS_Heading-3}

- N/A

# CREDIT MASTER Process Scope Design {#credit-master-process-scope-design .LS_Heading-1}

3.  

## Business Process for CREDIT MASTER流程图 {#business-process-for-credit-master流程图 .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| Process Step      | Process Step Description                                                                                                                | Business Role     | Transaction/App        |
+===================+=========================================================================================================================================+===================+========================+
| **001**           | Planners request to create a new customer credit or increase an existing customer credit amount when placing a sales order.             | Planner           | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **002**           | Finance admins search for Customer Credit Master Data in the system                                                                     | AR Admin          | Manage Credit Accounts |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **003**           | Finance admin fill credit update form and send to finance manage to approve, out of SAP, it can be done by hard copy document or email. | AR Admin          | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **004**           | Decide if the request gets approved or not                                                                                              | Finance Manager   | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **005**           | Create or update the customer credit master upon approval                                                                               | AR Admin          | Manage Credit Accounts |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **006**           | Notify the planner about the approval status.                                                                                           | AR Admin          | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
|                                                                                                                                                                                                          |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **流程步骤​​**      | **​​流程步骤​​​​**                                                                                                                            | **​​业务角色**      | **​​事务代码/应用**      |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **001**           | 计划员在下达销售订单时，会申请创建新的客户信用额度或提高现有客户的信用额度。                                                            | 计划员            | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **002**           | 财务管理员在系统中查询客户信用主数据。                                                                                                  | 应收账款管理员    | 管理信用账户           |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **003**           | 财务管理员填写信用更新表，并发送给财务经理审批。此操作在 SAP 系统外进行，可通过纸质文件或邮件完成。                                     | 应收账款管理员    | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **004**           | 判断该申请是否获批。                                                                                                                    | 财务经理          | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **005**           | 获批后，创建或更新客户信用主数据。                                                                                                      | 应收账款管理员    | 管理信用账户           |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+
| **006**           | 将审批状态通知计划员。                                                                                                                  | 应收账款管理员    | N/A                    |
+-------------------+-----------------------------------------------------------------------------------------------------------------------------------------+-------------------+------------------------+

## HC Functional Requirements {#hc-functional-requirements-2 .LS_Heading-3}

- Require the Credit limit only calculate the open deliveries and open invoice.(But system standard function calculate Open Orders + Open Deliveries+Open Invoice) Maybe we need to use credit exposure with credit limit to control the credit

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-1 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-2 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-2 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-2 .LS_Heading-3}

- N/A

# CUSTOMER MATERIAL MASTER Process Scope Design {#customer-material-master-process-scope-design .LS_Heading-1}

4.  

## Business Process for CUSTOMER MATERIAL MASTER流程图 {#business-process-for-customer-material-master流程图 .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| Process Step      | Process Step Description                                                                                                     | Business Role        | Transaction/App           |
+===================+:=============================================================================================================================+======================+===========================+
| **001**           | Search for Customer Material Master Data in the system                                                                       | **Planner**          | Manage customer materials |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| **002**           | Decide if the customer material master has existed already                                                                   | **Planner**          | N/A                       |
|                   |                                                                                                                              |                      |                           |
|                   | - If yes, proceed to step 003.                                                                                               |                      |                           |
|                   |                                                                                                                              |                      |                           |
|                   | - If no, proceed to step 005.                                                                                                |                      |                           |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| **003**           | Decide if there is any data change required                                                                                  | **Planner**          | N/A                       |
|                   |                                                                                                                              |                      |                           |
|                   | - If yes, proceed to step 004.                                                                                               |                      |                           |
|                   |                                                                                                                              |                      |                           |
|                   | - If no, end.                                                                                                                |                      |                           |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| **004**           | Update an existing customer material master if the data has existed in the SAP system and there is a data change requirement | **Planner**          | Manage customer materials |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| **005**           | If there is no existing data found in the system, create a new customer material master.                                     | **Planner**          | Manage customer materials |
|                   |                                                                                                                              |                      |                           |
|                   | *\* Need to map 1 customer material number to 1 HC SAP material number.*                                                     |                      |                           |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
|                                                                                                                                                                                                     |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| **流程步骤​​**      | **​​流程步骤​​​​**                                                                                                                 | **​​业务角色**         | **​​事务代码/应用**         |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| 001               | 在系统中查询客户物料主数据                                                                                                   | 计划员               | 管理客户物料              |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| 002               | 判断该客户物料主数据是否已存在                                                                                               | 计划员               | N/A                       |
|                   |                                                                                                                              |                      |                           |
|                   | - 若是，进入步骤 003。                                                                                                       |                      |                           |
|                   |                                                                                                                              |                      |                           |
|                   | - 若否，进入步骤 005。                                                                                                       |                      |                           |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| 003               | 判断是否需要更改数据                                                                                                         | 计划员               | N/A                       |
|                   |                                                                                                                              |                      |                           |
|                   | - 若是，进入步骤 004。                                                                                                       |                      |                           |
|                   |                                                                                                                              |                      |                           |
|                   | - 若否，流程结束。                                                                                                           |                      |                           |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| 004               | 若 SAP 系统中已存在该数据且需要更改，更新现有客户物料主数据                                                                  | 计划员               | 管理客户物料              |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+
| 005               | 若系统中未找到现有数据，创建新的客户物料主数据。                                                                             | 计划员               | 管理客户物料              |
|                   |                                                                                                                              |                      |                           |
|                   | - 需将 1 个客户物料编号与 1 个 HC SAP 物料编号相对应。                                                                       |                      |                           |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+----------------------+---------------------------+

-+

## HC Functional Requirements {#hc-functional-requirements-3 .LS_Heading-3}

- N/A

## HC Delegation Of Authority {#hc-delegation-of-authority-2 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-2 .LS_Heading-3}

- Customer material master \-\-- Account Group

+:---------------:+:------------------------------:+:---:+:-------------------:+:------------------------:+:------------------------------------------------------------------------------------------------------------------------------------------------------:+
| Cust. Acct. Grp | Description                    | Ext | Number range object | Number Range             | Remarks                                                                                                                                                |
+-----------------+--------------------------------+-----+---------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| 0001            | Sold-to Party                  |     | 02                  | 0002000002 -- 0002999999 | Used for all third party customers                                                                                                                     |
+-----------------+--------------------------------+-----+---------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| 0002            | Ship-to party                  |     | 02                  | 0002000002 -- 0002999999 | Used to create delivery location of a customer if the customer has multiple delivery locations/addresses.                                              |
+-----------------+--------------------------------+-----+---------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| CPD             | One-time Customer.             | X   | 00                  | 0000000001 -- 0000001000 | A common number used for a customer who very seldom purchase from Home Control (i.e. Home Control does not expect recurring sales from this customer). |
|                 |                                |     |                     |                          |                                                                                                                                                        |
|                 | (int. no. assignment)          |     |                     |                          |                                                                                                                                                        |
+-----------------+--------------------------------+-----+---------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| ZACC            | Bill-to Payer                  |     | 02                  | 0002000002 -- 0002999999 |                                                                                                                                                        |
+-----------------+--------------------------------+-----+---------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| ZOEM            | Customer OEM/ODM               | X   | 01                  | 0000100000 -- 0000999999 | For OEM/ODM Vendor number same as customer                                                                                                             |
+-----------------+--------------------------------+-----+---------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| 120             | Intern partner with ic billing | X   | 01                  | 0000100000 -- 0000999999 | 公司间客户 使用 company code                                                                                                                           |
|                 |                                |     |                     |                          |                                                                                                                                                        |
|                 |                                |     |                     |                          | Inter-Company use                                                                                                                                      |
+-----------------+--------------------------------+-----+---------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

- Pricing master

+:---------------:+:-------------------:+:---------------------:+:----------------:+:---------------:+:------------------------:+
| Price condition | Description         | Condition class       | Calculation Type | Access sequence | Remark                   |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
|                 | Price No.Man.Proc.  | Price                 | Quantity         | ZPRO            |                          |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| PPR0            | Net price           | Price                 | Quantity         | ZPRO            | Net price                |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| TTX1            | Output Tax          | Taxes                 | Percentage       | ZWST            | TTX1                     |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| ZGST            | GST                 | Taxes                 | Percentage       | ZWST            | SG21 tax                 |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
|                 | special net deal    | Price                 | Quantity         | ZPRO            | 待定                     |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| PMP0            | Manual price        | Price                 | Fixed amount     | ZPRO            | 用于Credit memo 手工创建 |
|                 |                     |                       |                  |                 |                          |
|                 |                     |                       |                  |                 | 后续使用PPR0             |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| DCD1            | Cash discount       | Discount or surcharge | Percentage       | 　              |                          |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| PCO1            | Cost                | Price                 | Quantity         | 　              |                          |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| PI01            | Inter-company Price | Price                 | Quantity         |                 | 公司间价格               |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| PCIP            | Internal Price      | Price                 |                  |                 | Standard Cost            |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| YZWR            | Down Pay/Settlement |                       |                  |                 |                          |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| HD00            | Freight cost        |                       |                  |                 | 在SO 里直接加            |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| Z001            | Tax                 |                       |                  |                 | BE company特殊税相关要求 |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+
| Z002            | Tax                 |                       |                  |                 | BE company特殊税相关要求 |
+-----------------+---------------------+-----------------------+------------------+-----------------+--------------------------+

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-3 .LS_Heading-3}

- N/A

## 1Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-3 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-3 .LS_Heading-3}

- N/A

# Free Goods Rate Process Scope Design {#free-goods-rate-process-scope-design .LS_Heading-1}

5.  

## Business Process for Free Goods Rate 流程图 {#business-process-for-free-goods-rate-流程图 .LS_Heading-3}

![](media/media/image6.emf)

## Business Process Steps {#business-process-steps-4 .LS_Heading-3}

+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| Process Step      | Process Step Description                                                                       | Business Role     | Transaction/App   |
+===================+================================================================================================+===================+===================+
| **001**           | Planners find the Free Goods Rate need creating after receiving the PPIA from Account manager. | Planner           |                   |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **002**           | Planners search the data in system to check if the data exists or not .                        | Planner           | Manage Free Goods |
|                   |                                                                                                |                   |                   |
|                   | If yes, go to step 003                                                                         |                   |                   |
|                   |                                                                                                |                   |                   |
|                   | If not, go to step 004.                                                                        |                   |                   |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **003**           | Planners check if the data needs changing.                                                     | Planner           | Manage Free Goods |
|                   |                                                                                                |                   |                   |
|                   | If yes, go to Step 004.                                                                        |                   |                   |
|                   |                                                                                                |                   |                   |
|                   | If not , process ends.                                                                         |                   |                   |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **004**           | Planners create or update the free goods rate if needed.                                       | Planner           | Manage Free Goods |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
|                                                                                                                                                            |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **流程步骤​​**      | **​​流程步骤​​​​**                                                                                   | **​​业务角色**      | **​​事务代码/应用** |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **001**           | 计划员在收到客户经理的 PPIA 后，发现需要创建赠品比例。                                         | Planner           | N/A               |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **002**           | 计划员在系统中搜索数据，检查该数据是否存在。                                                   | Planner           | 管理赠品          |
|                   |                                                                                                |                   |                   |
|                   | 若存在，进入步骤 003；\                                                                        |                   |                   |
|                   | 若不存在，进入步骤 004。                                                                       |                   |                   |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **003**           | 规划人员检查该数据是否需要修改。                                                               | Planner           | 管理赠品          |
|                   |                                                                                                |                   |                   |
|                   | 若需要，进入步骤 004；                                                                         |                   |                   |
|                   |                                                                                                |                   |                   |
|                   | 若不需要，流程结束。                                                                           |                   |                   |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+
| **004**           | 若有需要，计划人员创建或更新赠品比例。                                                         | Planner           | 管理赠品          |
+-------------------+------------------------------------------------------------------------------------------------+-------------------+-------------------+

## HC Functional Requirements {#hc-functional-requirements-4 .LS_Heading-3}

- N/A

## HC Delegation Of Authority {#hc-delegation-of-authority-3 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-3 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-4 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-4 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-4 .LS_Heading-3}

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

+-------------------------+---------------------------------------------------------+--------------------------------------+--------------------------+
| **Business Role**       | **Role Description**                                    | **Authorization Restrictions**       | **Baseline ZRS Role(s)** |
|                         |                                                         |                                      |                          |
|                         |                                                         | **(Tcodes)**                         |                          |
+=========================+=========================================================+======================================+==========================+
| **Planner**             | Search Pricing Master Data                              | VK13,Manage prices-sales,            | Z_Planner­\_CN            |
|                         |                                                         |                                      |                          |
|                         | Create, modify and search Customer Material Master Data | BP,Manage Customer Master Data       |                          |
|                         |                                                         |                                      |                          |
|                         | Create Contract                                         | VA43,Manage Sales contract,          |                          |
|                         |                                                         |                                      |                          |
|                         | Create modify and display Sales Order                   | VA01,VA02.VA03,                      |                          |
|                         |                                                         |                                      |                          |
|                         | Create modify and display delivery                      | Manage Sales Order,                  |                          |
|                         |                                                         |                                      |                          |
|                         | Order list report                                       | Manager Sales Order-Version 2        |                          |
|                         |                                                         |                                      |                          |
|                         | Blocked orders report                                   | VL01N,VL02N,VL03N                    |                          |
|                         |                                                         |                                      |                          |
|                         | Overdue orders report                                   | Manage Outbound Deliveries,          |                          |
|                         |                                                         |                                      |                          |
|                         | Delivery list report                                    | List Sales Orders                    |                          |
|                         |                                                         |                                      |                          |
|                         | General delivery list report                            | VA05,                                |                          |
|                         |                                                         |                                      |                          |
|                         |                                                         | VL06O                                |                          |
+-------------------------+---------------------------------------------------------+--------------------------------------+--------------------------+
| **AR Admin**            | Search Customer Master Data                             | BP                                   | Z_AR_Admin_CN            |
|                         |                                                         |                                      |                          |
|                         | Create and update the Pricing Master                    | VK13,Manage Prices-Sales,            |                          |
|                         |                                                         |                                      |                          |
|                         | Pricing report                                          | Analyze Credit Exposure              |                          |
|                         |                                                         |                                      |                          |
|                         | Credit Limit Overview                                   |                                      |                          |
+-------------------------+---------------------------------------------------------+--------------------------------------+--------------------------+
| **Finance Admin**       | Create, modify and search Credit Master Data            | Manage Credit Account ,              | Z_Finance_Admin_CN       |
|                         |                                                         |                                      |                          |
|                         | Credit Master sheet report                              | BP,Analyze Credit Exposure,          |                          |
|                         |                                                         |                                      |                          |
|                         | Customer credit records                                 |                                      |                          |
+-------------------------+---------------------------------------------------------+--------------------------------------+--------------------------+
| Master Data Team Member | Create, update and display Customer Master              | BP,Manage Customer Master Data,      | Z_Master_Data_CN         |
|                         |                                                         |                                      |                          |
|                         | Pricing report                                          | Manage Mass Maintenance,             |                          |
|                         |                                                         |                                      |                          |
|                         | Credit Master sheet report                              | Manage Business Partner-Master Data, |                          |
|                         |                                                         |                                      |                          |
|                         | Customer credit records                                 | Manage Customer Materials,           |                          |
|                         |                                                         |                                      |                          |
|                         | Customer material info records                          | Export Master Data-Business Partner  |                          |
|                         |                                                         |                                      |                          |
|                         | Customer master data records                            |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | Customer list report                                    |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | Mass Maintenance: Customer                              |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | Display change to Customer                              |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | Customer Master Data comparison                         |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | Customer Block/Unblock                                  |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | Credit Limit Overview                                   |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | List Customer-Material-Info                             |                                      |                          |
|                         |                                                         |                                      |                          |
|                         | Display Conditions Using Index                          |                                      |                          |
+-------------------------+---------------------------------------------------------+--------------------------------------+--------------------------+
|                         |                                                         |                                      |                          |
+-------------------------+---------------------------------------------------------+--------------------------------------+--------------------------+
|                         |                                                         |                                      |                          |
+-------------------------+---------------------------------------------------------+--------------------------------------+--------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

N/A

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  ------------------------------------------------------------------------------
  **SAP App**                     **Description / Usage**
  ------------------------------- ----------------------------------------------
  Manage customer master data     To export customer master data

  Manage customer material        To export customer material data

  Manage prices -- sales          To export pricing conditions

  Credit Limit Utilization        To display the credit usage

  Display Credit Management Log   To display the log of credit usage

  Analyze Credit Exposure         To analyze all credit accounts usage
  ------------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                                                          |
+----------------------------------+---------------------------------------------+----------------+------------------+----------------+----------------+
| **Report Name**                  | **Description**                             | **Key Files**  | **Std.**         | **Complexity** | **Comment**    |
|                                  |                                             |                |                  |                |                |
|                                  |                                             |                | **SAP App/Rprt** |                |                |
+==================================+=============================================+:===============+:=================+:===============+:===============+
| Pricing Condition Changes Report | To show the prices changes of each material |                | Next Phrase      | Low            | Customized     |
+----------------------------------+---------------------------------------------+----------------+------------------+----------------+----------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                                                                                      |
+-------------------+--------------------------------+-------------------+-------------------+------------------------------------------------------------------------+
| **Interface**     | **Description**                | **In Scope**      | **Complexity**    | **Comments**                                                           |
+===================+================================+===================+===================+========================================================================+
| Pricing condition | To show the changes of pricing |                   | Low               | Jean Ong needs this , but put this priority to be low(in next phrase). |
+-------------------+--------------------------------+-------------------+-------------------+------------------------------------------------------------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

范围内需要切换的数据如下

+----------------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                                  |
+-------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| **Data**          | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\      | **Complexity** |
|                   |                   |                           |                            | (# items)**    |                |
+===================+===================+===========================+============================+================+================+
| Customer          |                   | Low                       | Low                        | TBD            |                |
+-------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| Price condition   |                   | Low                       | Low                        | TBD            |                |
+-------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| Credit account    |                   | Low                       | Low                        | TBD            |                |
+-------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| Customer material |                   | Low                       | Low                        | TBD            |                |
+-------------------+-------------------+---------------------------+----------------------------+----------------+----------------+

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
| **增强项​​**       | **​​描述​​**         | **​​复杂度​​**       | **​​在范围内​​**     | **​​注释​​**                |
+------------------+------------------+------------------+------------------+-------------------------+
| N/A              |                  |                  |                  |                         |
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
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **表单​​**          | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

## Workflows {#workflows .LS_Heading-3}

The following workflows have been identified as in scope:

以下工作流被纳入范围：

+--------------------------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                                              |
+------------------------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**                       | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+====================================+===================+===================+===================+===================+
| Pricing Condtion Approval Workflow | Std Workflow      | Med               | Yes               |                   |
+------------------------------------+-------------------+-------------------+-------------------+-------------------+
|                                    |                   |                   |                   |                   |
+------------------------------------+-------------------+-------------------+-------------------+-------------------+
| **​​灵活工作流​​**                     | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+------------------------------------+-------------------+-------------------+-------------------+-------------------+
| ​​条件记录审批工作流​​                 | 标准工作流        | 中等              | 是                |                   |
+------------------------------------+-------------------+-------------------+-------------------+-------------------+
|                                    |                   |                   |                   |                   |
+------------------------------------+-------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow  ![](media/media/image7.png){width="6.003662510936133in" height="2.5246161417322837in"} {#legend-for-process-flow .LS_Heading-1}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
