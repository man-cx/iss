**Delivery Processing**

**出库交货流程**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_SD03_Delivery Processing**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

        Warner Yu                SD Lead                10/08/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. Delivery Processing [5](#delivery-processing)](#delivery-processing)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [5](#business-reason)](#business-reason)

[2.3 Business Benefits [5](#business-benefits)](#business-benefits)

[3. Process Scope Design [6](#process-scope-design)](#process-scope-design)

[3.1 Business Process for Delivery Process 流程图 [6](#business-process-for-delivery-process-流程图)](#business-process-for-delivery-process-流程图)

[3.1.1 Business Process Steps [6](#business-process-steps)](#business-process-steps)

[3.2 HC Functional Requirements [7](#hc-functional-requirements)](#hc-functional-requirements)

[3.3 HC Delegation Of Authority [7](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.4 Standard Documents / Settings [7](#standard-documents-settings)](#standard-documents-settings)

[3.5 Design Considerations / Key Assumptions [7](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.6 Cross Functional Integration Dependencies [7](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.7 Support / Closing Considerations [7](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [8](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [8](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [8](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [8](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [8](#reports)](#reports)

[6.1.1 Standard Reports [8](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [9](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [9](#interfaces)](#interfaces)

[6.3 Conversions [9](#conversions)](#conversions)

[6.4 Enhancements [10](#enhancements)](#enhancements)

[6.5 Forms [10](#forms)](#forms)

[6.6 Workflows [10](#workflows)](#workflows)

[7. Legend for Process Flow [11](#legend-for-process-flow)](#legend-for-process-flow)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       29/07/2025

       2.0                 Change after reviewing                  15/08/2025

                                                              
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

# Delivery Processing {#delivery-processing .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

Through standardized management of outbound deliveries, enterprises can achieve end-to-end visibility from sales to goods dispatch, improve logistics efficiency, and ensure financial accuracy.

## Business Reason {#business-reason .LS_Heading-3}

The Outbound Delivery is a core document in the SAP SD module for managing goods issue, acting as a key link connecting sales orders and actual goods dispatch.

## Business Benefits {#business-benefits .LS_Heading-3}

- Ensure the accuracy of shipments

- Optimize logistics processes

- Real-time inventory management

- Integration of financial and business operations

- Provide a basis for management

# Process Scope Design {#process-scope-design .LS_Heading-1}

1.  

## Business Process for Delivery Process 流程图 {#business-process-for-delivery-process-流程图 .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Process Step   Process Step Description                                                                                                           Transaction/App     Business Role
  -------------- ---------------------------------------------------------------------------------------------------------------------------------- ------------------- ---------------
  001            Check delivery due list based on shipping point                                                                                    VL10C               Planner

  002            Planner will create an Outbound Delivery with the SO reference and print the Delivery Note from the SAP system at the same time.   VL01N               Planner

  003            Planner will provide Logistics with the daily Shipping Plan in the format of Excel.                                                N/A                 Planner

  004            Logistics will book and arrange trucks accordingly.                                                                                N/A                 Planner

  005            Logistics will inform the planner about the delivery status (transportations are ready).                                           N/A                 Logistics

  006            Planner will pick                                                                                                                  VL02N               Logistics

  007            Planner will post a Goods Issue in the SAP system.                                                                                 VL02N               Planner

                                                                                                                                                                        

  **流程步骤​​**   **​​流程说明**                                                                                                                       **​​事务代码/应用​​**   **​​业务角色​​**

  001            基于装运点检查待交付清单                                                                                                           VL10C               Planner

  002            计划员将参考销售订单（SO）创建外向交货，同时从 SAP 系统打印交货单。                                                                VL01N               Planner

  003            计划员将以 Excel 格式向物流提供每日装运计划。                                                                                                          Planner

  004            物流将据此预订并安排卡车。                                                                                                         N/A                 Planner

  005            物流将向计划员告知交付状态（运输已准备就绪）。                                                                                     N/A                 Logistics

  006            计划员将进行拣货。                                                                                                                 VL02N               Logistics

  007            计划员将在 SAP 系统中过账发货。                                                                                                    VL02N               Planner
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- User require that the Pick Quantity equals to Delivery Quantity by default.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Cancel Picking process in Outbound Delivery.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- N/A

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

+-------------------+---------------------------+--------------------------------+--------------------------+
| **Business Role** | **Role Description**      | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+===================+===========================+================================+==========================+
| **Planner**       | Create Outbound Delivery  |                                | Z_Planner                |
|                   |                           |                                |                          |
|                   | Modify Outbound Delivery  |                                |                          |
|                   |                           |                                |                          |
|                   | Display Outbound Delivery |                                |                          |
|                   |                           |                                |                          |
|                   | Outbound Delivery Monitor |                                |                          |
+-------------------+---------------------------+--------------------------------+--------------------------+
|                   |                           |                                |                          |
+-------------------+---------------------------+--------------------------------+--------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------
  LF Outbound Delivery    

  LR Return Delivery      

                          

                          

                          
  -----------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **SAP App**                                     | **Description / Usage**                                                                                                                                                                                                                                        |
+=================================================+================================================================================================================================================================================================================================================================+
| Analyze Delivery Logs                           | You can use this app to check system messages that have been logged during the collective creation run of deliveries, regardless of whether you started the creation run online or in the background.                                                          |
+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Analyze Delivery Performance Shipped as Planned | This app allows you to monitor the current delivery performance within your organization, so you can keep track of customer satisfaction and retention                                                                                                         |
+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Sales Volume Flexible Analysis                  | You can use this app to gain an understanding of the monthly sales volume.                                                                                                                                                                                     |
+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Sales Volume Check Open Sales                   | With this app, you as a sales manager can check your sales volume in comparison with previous months, with the additional insight of open orders and open deliveries for the current month.                                                                    |
|                                                 |                                                                                                                                                                                                                                                                |
|                                                 | This enables you to see at a glance how the current month\'s sales volume relates to the previous month, and shows you where you can still increase your sales volume in the current period, for example, open orders, open billing requests, open deliveries. |
+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Sales Volume Open Sales by Org                  | With this app, you as a sales manager can check your sales volume in comparison with previous months, with the additional insight of open orders and open deliveries for the current month.                                                                    |
|                                                 |                                                                                                                                                                                                                                                                |
|                                                 | This enables you to see at a glance how the current month\'s sales volume relates to the previous month, and shows you where you can still increase your sales volume in the current period, for example, open orders, open billing requests, open deliveries. |
+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+-------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                       |
+-----------------+----------------------+----------------+------------------+----------------+---------------------+
| **Report Name** | **Description**      | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                 |                      |                |                  |                |                     |
|                 |                      |                | **SAP App/Rprt** |                |                     |
+:================+:=====================+:===============+:=================+:===============+:====================+
| ZSD007          | Deliveries follow-up |                | No               | Medium         |                     |
+-----------------+----------------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                 |
+------------------+------------------+------------------+------------------+--------------------+
| **Interface**    | **Description**  | **In Scope**     | **Complexity**   | **Comments**       |
+:=================+:=================+:=================+:=================+:===================+
| NA               |                  |                  |                  |                    |
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
|               |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| N/A           |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|               |                   |                           |                            |               |                |
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
| **增强项​​**       | **​​描述​​**         | **​​复杂度​​**       | **​​在范围内​​**     | **​​注释​​**                |
+------------------+------------------+------------------+------------------+-------------------------+
| N/A              |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+
|                  |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+

## Forms {#forms .LS_Heading-3}

The following forms have been identified as in scope:

+-----------------------------------------------------------------------------------------------------------+
| **Forms**                                                                                                 |
+-------------------+---------------------------+-------------------+-------------------+-------------------+
| **Form**          | **Description**           | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===========================+===================+===================+===================+
| Delivery Note     | EN version for US Company | Small             |                   |                   |
+-------------------+---------------------------+-------------------+-------------------+-------------------+
|                   |                           |                   |                   |                   |
+-------------------+---------------------------+-------------------+-------------------+-------------------+
| **表单​​**          | **​​描述​​**                  | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+---------------------------+-------------------+-------------------+-------------------+
| 出库交货单        | 只有美国使用              | 低                |                   |                   |
+-------------------+---------------------------+-------------------+-------------------+-------------------+
|                   |                           |                   |                   |                   |
+-------------------+---------------------------+-------------------+-------------------+-------------------+

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

# Legend for Process Flow ![](media/media/image3.png){width="6.003662510936133in" height="2.5246161417322837in"} {#legend-for-process-flow .LS_Heading-1}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
