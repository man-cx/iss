**FICO Master Data**

**FICO CO主数据**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: CO_DD_001 Master Data**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

       Frey Zheng               FICO Lead               08/11/2025
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

[2. CO Master Data [5](#co-master-data)](#co-master-data)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [5](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[3. Process Scope Design [7](#process-scope-design)](#process-scope-design)

[3.1 Maintain Cost Centers [7](#maintain-cost-centers)](#maintain-cost-centers)

[3.1.1 Business Process Steps [7](#business-process-steps)](#business-process-steps)

[3.2 Maintain Cost Center Groups/ Hierarchy [8](#maintain-cost-center-groups-hierarchy)](#maintain-cost-center-groups-hierarchy)

[3.3 Maintain Profit Center [10](#maintain-profit-center)](#maintain-profit-center)

[3.3.1 Business Process Steps [10](#business-process-steps-1)](#business-process-steps-1)

[3.4 Maintain Profit center group/ hierarchy [11](#maintain-profit-center-group-hierarchy)](#maintain-profit-center-group-hierarchy)

[3.5 Project Management [12](#project-management)](#project-management)

[3.5.1 Business Process Steps [12](#business-process-steps-2)](#business-process-steps-2)

[3.6 Manage Cost Element Master [13](#manage-cost-element-master)](#manage-cost-element-master)

[3.6.1 Business Process Steps [13](#business-process-steps-3)](#business-process-steps-3)

[3.7 Manage Statistical Key Figures [14](#manage-statistical-key-figures)](#manage-statistical-key-figures)

[3.7.1 Business Process Steps [14](#business-process-steps-4)](#business-process-steps-4)

[3.8 HC Functional Requirements [15](#hc-functional-requirements)](#hc-functional-requirements)

[3.9 HC Delegation Of Authority [15](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.10 Standard Documents / Settings [15](#standard-documents-settings)](#standard-documents-settings)

[3.11 Design Considerations / Key Assumptions [15](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.12 Cross Functional Integration Dependencies [16](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.13 Support / Closing Considerations [16](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [16](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [16](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [16](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [16](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [16](#reports)](#reports)

[6.1.1 Standard Reports [16](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [17](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [17](#interfaces)](#interfaces)

[6.3 Conversions [17](#conversions)](#conversions)

[6.4 Enhancements [18](#enhancements)](#enhancements)

[6.5 Forms [18](#forms)](#forms)

[6.6 Workflows [18](#workflows)](#workflows)

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

#  CO Master Data {#co-master-data .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

The objective of Home Control Controlling Master Data Blueprint is to introduce greater controls over the creation and maintenance of controlling master data, including profit center, cost center and project. This Business Process Blueprint aims to:

- Define the codification for controlling master data (profit center, cost center,project)

- Design profit center/cost center hierarchy for Home Control.

- Reduce time spent on master data maintenance

At Home Control, profit center will be created for each product line. Cost center will be created for each department/ location where expenses are incurred. Project will be created for each R&D project and tooling/normal fixed asset.

## Business Reason {#business-reason .LS_Heading-3}

- Complexity of cost structure: Enterprises have diverse business activities and complex cost compositions. It is necessary to rely on CO master data to classify and refine cost management, clearly define the sources and destinations of different costs, so as to better understand the cost structure and identify cost drivers.

- Internal responsibility division: Master data such as cost centers can assign cost responsibilities to specific departments or business units, clarify the cost management responsibilities of each department, urge departments to pay attention to cost-effectiveness, and improve the enthusiasm and sense of responsibility in cost management.

- Demand for financial and business integration: The SAP CO module is closely integrated with other modules (such as FI, MM, PP, etc.), and CO master data is one of the key bridges to realize the integration of finance and business. Through unified master data, the consistency and continuity of business data and financial data are ensured, and the seamless connection between business processes and financial processes is realized.

## Business Benefits {#business-benefits .LS_Heading-3}

- Optimizing resource allocation: Based on accurate cost data, enterprises can identify key areas of resource consumption and inefficient links, adjust resource allocation reasonably, tilt resources toward high-value businesses and projects, and improve resource utilization efficiency.

- Enhancing cost control capabilities: By monitoring the occurrence of costs and expenses in real time, comparing actual costs with planned costs, enterprises can promptly detect cost deviations and take corrective measures, effectively control cost expenditures, and reduce operational costs.

- Improving decision-making accuracy: Providing reliable data support for decision-making enables enterprise management to make more informed decisions, reduce risks caused by decision-making errors, and enhance the enterprise\'s competitiveness and profitability.

- Increasing internal management efficiency: Standardizing cost accounting and management processes reduces manual operations and data errors, improves the efficiency of financial settlement and report preparation, and facilitates communication and collaboration between departments, thereby enhancing the overall operational management efficiency of the enterprise.

# Process Scope Design {#process-scope-design .LS_Heading-1}

##  Maintain Cost Centers {#maintain-cost-centers .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| Process Step                                                                                   | Business Role    | Transaction/App                 | Expected Results               |
+================================================================================================+==================+=================================+================================+
| 1.  Users raise request to CO administrator for new cost center master                         | N/A              | N/A                             | N/A                            |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 2.  Users fill cost center creation form. This form has the following information              | N/A              | N/A                             | N/A                            |
|                                                                                                |                  |                                 |                                |
| - Name, description                                                                            |                  |                                 |                                |
|                                                                                                |                  |                                 |                                |
| - Cost center category                                                                         |                  |                                 |                                |
|                                                                                                |                  |                                 |                                |
| - Hierarchy area (cost center group in the Standard Hierarchy)                                 |                  |                                 |                                |
|                                                                                                |                  |                                 |                                |
| - Company code                                                                                 |                  |                                 |                                |
|                                                                                                |                  |                                 |                                |
| - Profit center                                                                                |                  |                                 |                                |
|                                                                                                |                  |                                 |                                |
| - Functional Area                                                                              |                  |                                 |                                |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 3.  Verify cost center requirement base on posting required and analysis report                | CO Administrator | N/A                             | N/A                            |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 4.  If the request is accepted CO Administrator verifies whether cost center exists in system. | CO Administrator | Manage Cost Centers             | Query Cost Centers             |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 5.  If CO admin finds that cost center exist in system then he/she informs users               | CO Administrator | N/A                             | N/A                            |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 6.  CO Administrator creates cost center                                                       | CO Administrator | Manage Cost Centers             | Cost Centers is created        |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 7.  Cost center groups are updated                                                             | CO Administrator | Manage Global Hierarchies       | Cost center groups are updated |
|                                                                                                |                  |                                 |                                |
|                                                                                                |                  | (Type is Cost Center Hierarchy) |                                |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 8.  Inform BU new Cost center created                                                          | CO Administrator | N/A                             | N/A                            |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+
| 9.  If the request is rejected, CO Administrator informs relevant BU.                          | N/A              | N/A                             | N/A                            |
+------------------------------------------------------------------------------------------------+------------------+---------------------------------+--------------------------------+

## Maintain Cost Center Groups/ Hierarchy {#maintain-cost-center-groups-hierarchy .LS_Heading-3}

Cost center standard hierarchy is a cost center group that is required by the system during cost center creation. The standard hierarchy is a tree structure which contains all cost centers in a controlling area and reflects the organizational structure represented using Cost Center Accounting.

Standard hierarchy of Home Control is HC01

Standard cost center group naming convention:

+------------+---------------------------+---------------------------------------------------+----------------------------------------------------------------------------+
| **Sl No.** | **Digits**                | **Codification Logic**                            | **Example**                                                                |
+:===========+===========================+===================================================+============================================================================+
|            | 1st,2nd, 3rd & 4th digits | First Four digits will represent the company code | **SG21** Home Control Singapore Pte Ltd                                    |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **CN13** HC (Suzhou) Limited                                               |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **CN17**Home Control Solutions **US10** Premium Home Control Solutions LLC |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **BE10** Home Control Europe NV                                            |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **BR10** **Omni Remotes Do Brasil Ltda**                                   |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **HCIL** **Home Control International Limited**                            |
+------------+---------------------------+---------------------------------------------------+----------------------------------------------------------------------------+
|            | 5^th^ , 6^th^             | Fifth and sixth digits will represent the country | **SG** -- SG                                                               |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **CN** -- China                                                            |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **US** -- USA                                                              |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **BE** -- Belgium                                                          |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **BR -- Brazil**                                                           |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **UK- United Kingdom**                                                     |
+------------+---------------------------+---------------------------------------------------+----------------------------------------------------------------------------+
|            | 7^th^                     | Seventh digits will represent the functional area | **1** -Manufacturing                                                       |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **2** -- Sales                                                             |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **3** - G&A                                                                |
|            |                           |                                                   |                                                                            |
|            |                           |                                                   | **5** - R&D                                                                |
+------------+---------------------------+---------------------------------------------------+----------------------------------------------------------------------------+

Users can create many other cost center groups for their reporting and allocation purposes.

The cost center hierarchy is as follows

![](media/media/image3.emf)

1.  

    1.  

## Maintain Profit Center {#maintain-profit-center .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| Process Step                                                                                     | Business Role    | Transaction/App                   | Expected Results                 |
+==================================================================================================+==================+===================================+==================================+
| 1.  BU raises request to Head of Department and CFO of HOME CONTROL for approval                 | N/A              | N/A                               | N/A                              |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 2.  BU raises request to Controlling Administrator for new profit center master                  | N/A              | N/A                               | N/A                              |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 3.  Verify profit center requirement based on the need of postings and analysis reports.         | CO administrator | N/A                               | N/A                              |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 4.  If rejected, inform BU                                                                       | CO administrator | N/A                               | N/A                              |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 5.  If the request is accepted. CO administrator verifies whether profit center exists in system | CO administrator | Manage Profit Centers             | Query Profit Centers             |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 6.  Inform BU profit center already exists                                                       | CO administrator | N/A                               | N/A                              |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 7.  CO Administrator creates profit center                                                       | CO administrator | Manage Profit Centers             | Profit Center is created         |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 8.  Profit center groups are updated                                                             | CO administrator | Manage Global Hierarchies         | Profit center groups are updated |
|                                                                                                  |                  |                                   |                                  |
|                                                                                                  |                  | (Type is Profit Center Hierarchy) |                                  |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 9.  Inform BU new profit center created                                                          | CO administrator | N/A                               | N/A                              |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+
| 10. BU informs relevant parties of new profit center creation.                                   | N/A              | N/A                               | N/A                              |
+--------------------------------------------------------------------------------------------------+------------------+-----------------------------------+----------------------------------+

## Maintain Profit center group/ hierarchy {#maintain-profit-center-group-hierarchy .LS_Heading-3}

Profit center standard hierarchy is a profit center group that is required by system during profit center creation.

It comprises all profit centers for a given period belonging to a controlling area, and thus represents the whole enterprise.

At Home Control, profit center hierarchy is HC01

**Profit center hierarchy**

![](media/media/image5.png){width="3.8125in" height="1.6458333333333333in"}

## Project Management {#project-management .LS_Heading-3}

![](media/media/image6.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| Process Step                                                                       | Business Role    | Transaction/App                       | Expected Results   |
+====================================================================================+==================+=======================================+====================+
| 1.  BU raises request to Controlling Administrator for new project                 | N/A              | N/A                                   | N/A                |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| 2.  Verify Project requirement based on the need of postings and analysis reports. | CO administrator | N/A                                   | N/A                |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| 3.  If request is rejected, CO administrator informs BU                            | CO administrator | N/A                                   | N/A                |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| 4.  If the request is accepted CO administrator verifies Project exists in system  | CO administrator | Project Control - Enterprise Projects | Query Project      |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| 5.  Inform BU project already exists                                               | CO administrator | N/A                                   | N/A                |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| 6.  CO Administrator creates Project                                               | CO administrator | Project Control - Enterprise Projects | Project is created |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| 7.  Project is updated.                                                            | CO administrator | Project Control - Enterprise Projects | Project is updated |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+
| 8.  Inform BU new project is created.                                              | CO administrator | N/A                                   | N/A                |
+------------------------------------------------------------------------------------+------------------+---------------------------------------+--------------------+

## Manage Cost Element Master {#manage-cost-element-master .LS_Heading-3}

![](media/media/image7.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

+-----------------------------------------------------------------+------------------+--------------------------------------------------------------------+---------------------------------------+
| Process Step                                                    | Business Role    | Transaction/App                                                    | Expected Results                      |
+=================================================================+==================+====================================================================+=======================================+
| 1.  Primary cost element created automatically                  | CO Administrator | Manage G/L Account Master Data                                     | Primary cost element is created       |
+-----------------------------------------------------------------+------------------+--------------------------------------------------------------------+---------------------------------------+
| 2.  Update cost element group if required                       | CO Administrator | Primary cost element                                               | Cost element group is updated         |
+-----------------------------------------------------------------+------------------+--------------------------------------------------------------------+---------------------------------------+
| 3.  CO team require new secondary cost element to allocate cost | N/A              | N/A                                                                | N/A                                   |
+-----------------------------------------------------------------+------------------+--------------------------------------------------------------------+---------------------------------------+
| 4.  Check Secondary cost element already exist                  | CO Administrator | Manage G/L Account Master Data-G/L Account Type is Secondary Costs | Query G/L account                     |
+-----------------------------------------------------------------+------------------+--------------------------------------------------------------------+---------------------------------------+
| 5.  Create New Secondary Cost Element.                          | CO Administrator | Manage G/L Account Master Data-G/L Account Type is Secondary Costs | New Secondary Cost Element is created |
+-----------------------------------------------------------------+------------------+--------------------------------------------------------------------+---------------------------------------+
| 6.  Inform Controlling Team                                     | CO Administrator | N/A                                                                | N/A                                   |
+-----------------------------------------------------------------+------------------+--------------------------------------------------------------------+---------------------------------------+

## Manage Statistical Key Figures {#manage-statistical-key-figures .LS_Heading-3}

![](media/media/image8.emf)

## Business Process Steps {#business-process-steps-4 .LS_Heading-3}

+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+
| Process Step                                            | Business Role    | Transaction/App                | Expected Results                   |
+=========================================================+==================+================================+====================================+
| 1.  BU sent request for new SKF                         | N/A              | N/A                            | N/A                                |
+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+
| 2.  CO administrator verifies SKF requirement           | CO administrator | N/A                            | N/A                                |
+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+
| 3.  If rejected, CO administrator informs Business Unit | CO administrator | N/A                            | N/A                                |
+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+
| 4.  CO administrator verifies if SKF exists             | CO administrator | Manage Statistical Key Figures | Query Statistical Key Figures      |
+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+
| 5.  Inform BU SKF already exists                        | CO administrator | N/A                            | N/A                                |
+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+
| 6.  Create SKF                                          | CO administrator | Manage Statistical Key Figures | Statistical Key Figures is created |
+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+
| 7.  CO administrator informs BU for new SKF created     | CO administrator | N/A                            | N/A                                |
+---------------------------------------------------------+------------------+--------------------------------+------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- System should able to support generating financial statement at company code level as well as profit center level.

- System should able to analyze overhead costs according to where they were incurred within the organization.

- \- Cost capture at lowest unit level.

- \- In depth analysis of cost for a unit.

- System should able to analyze actual expense for each R&D project by year, by cost type

- 11 IC1 Other dev cost

- 21 IC2 Material (P)

- 22 IC2 Jigs & Equip

- 31 IC3 Tooling

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- The definitions of Cost Center Groups/ Hierarchy and Profit center group/ hierarchy are integrated into the global structure application, the Type is the Cost Center Hierarchy and Profit Center Hierarchy.

- Cost elements include primary cost elements and secondary cost elements,they are no longer maintained separately; instead, they are automatically created when G/L accounts are created, the G/L Account Type is Primary Costs or Revenue and Secondary Costs

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Master Data Synchronization: CO master data (e.g., cost centers) often aligns with organizational structures in other modules (e.g., HR org units, MM plants).

- Automatic Posting: Integration ensures business transactions in operational modules (MM, SD, PP) automatically generate corresponding CO postings without manual intervention.

- Reconciliation: Periodic reconciliation processes (e.g., FI-CO reconciliation) ensure data consistency between modules. Support / Closing Considerations

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

+-------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+
| **Business Role** | **Role Description**                                                                                                  | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+===================+=======================================================================================================================+================================+==========================+
| CO Administrator  | - Responsible to maintain profit center, cost center, cost element, project master data for whole Home Control group. | Std Roles                      | - BR_OVERHEAD_ACCOUNTANT |
+-------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------+--------------------------+

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

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **SAP App**                      **Description / Usage**
  -------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Manage Cost Element Groups       It is used to group cost elements with similar characteristics. Cost element groups can be used in information systems, for example, to define the row structure of reports, and the system calculates totals for each node in the report. They can also handle multiple cost elements simultaneously in transactions such as cost center planning, allocation or distribution, facilitating unified operation and analysis of a type of cost elements.

  Manage Profit Centers            Create, maintain, and query profit centers for profit accounting, asset analysis, and department performance evaluation.

  Manage Cost Centers              Create, maintain, and query cost centers, the smallest unit for cost aggregation and management.

  Manage Statistical Key Figures   created, changed, and displayed individually or collectively. They serve as the basis for internal allocation and indicator analysis.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
