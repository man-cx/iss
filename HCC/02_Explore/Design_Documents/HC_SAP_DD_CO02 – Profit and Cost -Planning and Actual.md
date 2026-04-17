**FICO Profit and Cost -Planning and Actual**

**FICO 利润与成本 - 计划与实际**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: CO_DD_002 Profit and Cost -Planning and Actual**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

       Frey Zheng               FICO Lead               08/15/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Jane Chen           Finance - Costing       

     Minting Wang              Finance            

      Sally Jin                Finance            

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. Profit and Cost -Planning and Actual [5](#profit-and-cost--planning-and-actual)](#profit-and-cost--planning-and-actual)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [5](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[3. Process Scope Design [6](#process-scope-design)](#process-scope-design)

[3.1 Manage Cost Center Planning [6](#manage-cost-center-planning)](#manage-cost-center-planning)

[3.1.1 Business Process Steps [6](#business-process-steps)](#business-process-steps)

[3.2 Manage Profit Center Planning [7](#manage-profit-center-planning)](#manage-profit-center-planning)

[3.2.1 Business Process Steps [7](#business-process-steps-1)](#business-process-steps-1)

[3.3 Manage Project Budgeting [8](#manage-project-budgeting)](#manage-project-budgeting)

[3.3.1 Business Process Steps [8](#business-process-steps-2)](#business-process-steps-2)

[3.4 Manage CO month end [9](#manage-co-month-end)](#manage-co-month-end)

[3.4.1 Business Process Steps [9](#business-process-steps-3)](#business-process-steps-3)

[3.5 HC Functional Requirements [9](#hc-functional-requirements)](#hc-functional-requirements)

[3.6 HC Delegation Of Authority [10](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.7 Standard Documents / Settings [10](#standard-documents-settings)](#standard-documents-settings)

[3.8 Design Considerations / Key Assumptions [10](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.9 Cross Functional Integration Dependencies [10](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.10 Support / Closing Considerations [10](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [11](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [11](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [11](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [11](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [11](#reports)](#reports)

[6.1.1 Standard Reports [11](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [12](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [12](#interfaces)](#interfaces)

[6.3 Conversions [12](#conversions)](#conversions)

[6.4 Enhancements [12](#enhancements)](#enhancements)

[6.5 Forms [13](#forms)](#forms)

[6.6 Workflows [13](#workflows)](#workflows)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       08/11/2025

                                                              

                                                              
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

- Major design issues that need to be resolved in order to move forward in Realize stage (e.g., Iprojects vs. Project Systems​)

- Place on the Issues Log, assign owner and due date, manage​ issue

- Complete Key Design Decision document and escalate (PMO then Executive Sponsor)

If you have any items that may withhold signature it is your responsibility to escalate as soon as possible

#  Profit and Cost -Planning and Actual {#profit-and-cost--planning-and-actual .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

Using the Import P&L Data SAP Fiori application, you can load a semicolon separated file for PLAN data into the SAP S/4HANA Cloud Public Edition application. A template is provided to ensure that the file is successfully loaded into the application.

The Universal Allocation scope item covers plan and actual allocations. For plan allocations of cost centers in overhead cost controlling, it covers the upload of cost center plan data and the execution of the plan allocation cycles. Annual planning is supported via cost redistribution through defined allocation cycles, by definition of sender and receiver rules by fixed amount and percentage. You can control your costs and compare plan and actual costs by allocating the cost elements to cost centers in overhead cost controlling.

## Business Reason {#business-reason .LS_Heading-3}

- Cost center planning forms part of the overall business planning process, and is prerequisite for full Profit and Loss planning.

- Cost center planning and Profit center planning will be done for Singapore and China companies.

  - Home Control Suzhou will be in-charge for planning figures of two companies in China (CN13 and CN17) and China cost centers of Home Control Singapore (SG21).

  - • Home Control Singapore will be in-charge for planning figure of Singapore cost centers of itself.

## Business Benefits {#business-benefits .LS_Heading-3}

- Enable load from any source system that can produce a flat file

- Access an SAP Fiori interface as a user with an authorized profile

<!-- -->

- Gain better control of costs with visibility into how actual costs compare with plan

# Process Scope Design {#process-scope-design .LS_Heading-1}

##  Manage Cost Center Planning {#manage-cost-center-planning .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+-------------------------------------------------------------------------------------------------------------------------------------------+---------------+-----------------------------------------------------------+-------------------------------------------------------------------------+
| Process Step                                                                                                                              | Business Role | Transaction/App                                           | Expected Results                                                        |
+===========================================================================================================================================+===============+===========================================================+=========================================================================+
| 1.  Planner initiates Planning preparation for new financial year Annually, users prepare yearly planning expense by department in Excel. | CO executive  | N/A                                                       | N/A                                                                     |
+-------------------------------------------------------------------------------------------------------------------------------------------+---------------+-----------------------------------------------------------+-------------------------------------------------------------------------+
| 2.  Upload cost center planning from template                                                                                             | CO executive  | Import Financial Plan Data ,template:Cost Center Planning | cost center planning is uploaded to the system.                         |
+-------------------------------------------------------------------------------------------------------------------------------------------+---------------+-----------------------------------------------------------+-------------------------------------------------------------------------+
| 3.  Run Plan Distribution                                                                                                                 | CO executive  | Manage Allocations                                        | The expense distributed from a common cost center to other cost centers |
|                                                                                                                                           |               |                                                           |                                                                         |
| If users want to allocate expense from a common cost center to other cost centers, they will execute this transaction                     |               | Allocation Type:Distribution                              |                                                                         |
+-------------------------------------------------------------------------------------------------------------------------------------------+---------------+-----------------------------------------------------------+-------------------------------------------------------------------------+
| 4.  Run Plan Assessment                                                                                                                   | CO executive  | Manage Allocations                                        | The expense assessed from a common cost center to other cost centers    |
|                                                                                                                                           |               |                                                           |                                                                         |
| If users want to assessment expense from a common cost center to other cost centers, they will execute this transaction                   |               | Allocation Type:Overhead Allocation                       |                                                                         |
+-------------------------------------------------------------------------------------------------------------------------------------------+---------------+-----------------------------------------------------------+-------------------------------------------------------------------------+

## Manage Profit Center Planning {#manage-profit-center-planning .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+---------------------------------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------+-----------------------------------------------------------------------------+
| Process Step                                                                                                              | Business Role | Transaction/App                                            | Expected Results                                                            |
+===========================================================================================================================+===============+============================================================+=============================================================================+
| 1.  Users will upload profit center planning data from Excel to SAP                                                       | CO executive  | Import Financial Plan Data template:Profit Center Planning | profit center planning is uploaded to the system                            |
+---------------------------------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------+-----------------------------------------------------------------------------+
| 2.  Run Plan Distribution                                                                                                 | CO executive  | Manage Allocations                                         | The revenue distributed from a common profit center to other profit centers |
|                                                                                                                           |               |                                                            |                                                                             |
| If users want to allocate revenue from a common profit center to other profit centers, they will execute this transaction |               | Allocation Type:Distribution                               |                                                                             |
+---------------------------------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------+-----------------------------------------------------------------------------+
| 3.  Run Plan Assessment                                                                                                   | CO executive  | Manage Allocations-                                        | The revenue assessed from a common cost center to other cost centers        |
|                                                                                                                           |               |                                                            |                                                                             |
| If users want to allocate revenue from a common profit center to other profit centers, they will execute this transaction |               | Allocation Type:Overhead Allocation                        |                                                                             |
+---------------------------------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------+-----------------------------------------------------------------------------+

## Manage Project Budgeting {#manage-project-budgeting .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

+----------------------------------------------+------------------+-------------------------------------------------------+------------------------------------------+
| Process Step                                 | Business Role    | Transaction/App                                       | Expected Results                         |
+==============================================+==================+=======================================================+==========================================+
| 1.  Requestor raise request for new budget   | Budget executive | N/A                                                   | N/A                                      |
+----------------------------------------------+------------------+-------------------------------------------------------+------------------------------------------+
| 2.  Upload budget from template              | Budget executive | Import Financial Plan Data template:Project Budgeting | Project budget is uploaded to the system |
+----------------------------------------------+------------------+-------------------------------------------------------+------------------------------------------+
| 3.  Send request to update budget to finance | Budget executive | N/A                                                   | N/A                                      |
+----------------------------------------------+------------------+-------------------------------------------------------+------------------------------------------+
| 4.  Approval budget                          | Budget executive | N/A                                                   | N/A                                      |
+----------------------------------------------+------------------+-------------------------------------------------------+------------------------------------------+
| 5.  Update budget                            | Budget executive | Import Financial Plan Data template:Project Budgeting | Project budget is updated                |
+----------------------------------------------+------------------+-------------------------------------------------------+------------------------------------------+
| 6.  Inform requestor                         | Budget executive | N/A                                                   | N/A                                      |
+----------------------------------------------+------------------+-------------------------------------------------------+------------------------------------------+

## Manage CO month end {#manage-co-month-end .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

+------------------------------------------------+---------------+----------------------------------------------------------+---------------------------------------------+
| Process Step                                   | Business Role | Transaction/App                                          | Expected Results                            |
+================================================+===============+==========================================================+=============================================+
| 1.  Settle Project                             | CO Executive  | Schedule Project Accounting Jobs                         | Project is settled                          |
|                                                |               |                                                          |                                             |
|                                                |               | job template:Actual Settlement: Projects (SAP)           |                                             |
+------------------------------------------------+---------------+----------------------------------------------------------+---------------------------------------------+
| 2.  Analyze Cost Center Report                 | CO Executive  | Cost Centers - Plan/Actual                               | Query the report Cost Centers - Plan/Actual |
+------------------------------------------------+---------------+----------------------------------------------------------+---------------------------------------------+
| 3.  FI/CO adjustment                           | CO Executive  | Reassign Costs and Revenues/Post General Journal Entries | Journal Entries are created                 |
+------------------------------------------------+---------------+----------------------------------------------------------+---------------------------------------------+
| 4.  Cost Allocation (Distribution, Assessment) | CO Executive  | Manage Allocations                                       | Query G/L account                           |
+------------------------------------------------+---------------+----------------------------------------------------------+---------------------------------------------+
| 5.  Cost allocation from CC to COPA            | CO Executive  | Run Allocations                                          | Cost allocation from CC to COPA             |
+------------------------------------------------+---------------+----------------------------------------------------------+---------------------------------------------+
| 6.  CO Reports                                 | CO Executive  | Market Segments - Plan/Actual                            | Query the report                            |
+------------------------------------------------+---------------+----------------------------------------------------------+---------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- System should support uploading of planning and forecast (e.g. in excel format).

- System should support different versions of budget and forecast. For example, annual planning, forecasting Quarter 1, Quarter 2, Quarter 3, Quarter 4

- System should support the ability to perform multiple overhead cost allocation simulations to facilitate budgeting of overhead allocation.

- System should record budget and forecast data for each R&D project

- System should support reporting of actual against planning and/or forecast and budget utilization by:

> \- company
>
> \- cost center

- System should support cost allocation from department to market segment to get net profit

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- In SAP Cloud ERP, all cost center planning, profit center planning, and project budgets are integrated into a single application called \"Import Financial Plan Data\". Data can be uploaded into the system using different templates.

- The allocation and apportionment functions for cost centers, profit centers, and Margin Analysis are all integrated into one application named \"Manage Allocations\". By selecting different Allocation Contexts and Allocation Types, the allocation and apportionment functions for cost centers, profit centers, and Margin Analysis can be realized.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Cost center planning provides a cost control foundation for profit center planning,

- Project budgets need to be integrated into the enterprise\'s overall cost and profit planning.

- Meanwhile, the cross-functional integration of monthly cost closing is a summary and verification of the implementation of various plans, which relies on the collaborative cooperation of various departments to ensure the accuracy of enterprise cost accounting and the reliability of financial information.

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

+-------------------+--------------------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| **Business Role** | **Role Description**                                                                                         | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+===================+==============================================================================================================+================================+==========================+
| CO executive      | - Responsible to upload data planning figure and execute allocation cycle as well as CO Month End activities | Std Roles                      | - BR_OVERHEAD_ACCOUNTANT |
+-------------------+--------------------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| Budget executive  | - Responsible to maintain project budgeting                                                                  |                                | - BR_OVERHEAD_ACCOUNTANT |
+-------------------+--------------------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+

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

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **SAP App**                         **Description / Usage**
  ----------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Project Cost Report - Plan/Actual   Compare the planned cost and actual cost of a project, and analyze the budget execution and project cost

  Cost Centers - Plan/Actual          Check the difference between the planned cost and actual expenditure of each cost center, and monitor the effect of cost.

  P&L - Plan/Actual                   Compare the planned and actual revenue, cost and profit of the entire enterprise or department, and evaluate the achievement of profit goals

  Market Segments - Plan/Actual       Compare the planned and actual performance of each market segment by product, customer and other dimensions, so as to optimize resource allocation and marketing strategies.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+--------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                  |
+-----------------+-----------------+----------------+------------------+----------------+---------------------+
| **Report Name** | **Description** | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                 |                 |                |                  |                |                     |
|                 |                 |                | **SAP App/Rprt** |                |                     |
+:================+=================+:===============+:=================+:===============+:====================+
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
