**Demand and Material Requirements Planning**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: PP_DD_002 Demand and Material Requirements Planning**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Joe Wu                  PP Lead                08/01/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

     Nancy Zhang             Supply Chain         

      Lin Zhang              Procurement          

     Xiaoqin Zhuo            Procurement          

      Cherry Qu               Purchasing          

     Yu Xiaodong              Purchasing          

      Jelly Ding              Purchasing          

      Sara Wang                Planner            

      Irene Liu                Planner            

      Rocky Cai            Project Manager        

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [4](#design-document-approval-options)](#design-document-approval-options)

[2. Scenarios [4](#scenarios)](#scenarios)

[2.1 FG Planning [5](#fg-planning)](#fg-planning)

[**2.1.1** **Purpose** [5](#purpose)](#purpose)

[**2.1.2** **Business Reason** [5](#business-reason)](#business-reason)

[**2.1.3** **Business Benefits** [5](#business-benefits)](#business-benefits)

[**2.1.4** **Business Process Flow** [6](#business-process-flow)](#business-process-flow)

[**2.1.5** **Business Process Steps** [7](#business-process-steps)](#business-process-steps)

[**2.1.6** **HC Functional Requirements** [7](#hc-functional-requirements)](#hc-functional-requirements)

[**2.1.7** **HC Delegation Of Authority** [8](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[**2.1.8** **Standard Documents / Settings** [8](#standard-documents-settings)](#standard-documents-settings)

[**2.1.9** **Design Considerations / Key Assumptions** [8](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[**2.1.10** **Cross Functional Integration Dependencies** [8](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[**2.1.11** **Support / Closing Considerations** [8](#support-closing-considerations)](#support-closing-considerations)

[2.2 MRP Run [8](#mrp-run)](#mrp-run)

[**2.2.1** **Purpose** [8](#purpose-1)](#purpose-1)

[**2.2.2** **Business Reason** [9](#business-reason-1)](#business-reason-1)

[**2.2.3** **Business Benefits** [9](#business-benefits-1)](#business-benefits-1)

[**2.2.4** **Business Process Flow** [10](#business-process-flow-1)](#business-process-flow-1)

[**2.2.5** **Business Process Steps** [11](#business-process-steps-1)](#business-process-steps-1)

[**2.2.6** **HC Functional Requirements** [11](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[**2.2.7** **HC Delegation Of Authority** [11](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[**2.2.8** **Standard Documents / Settings** [11](#standard-documents-settings-1)](#standard-documents-settings-1)

[**2.2.9** **Design Considerations / Key Assumptions** [12](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[**2.2.10** **Cross Functional Integration Dependencies** [12](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[**2.2.11** **Support / Closing Considerations** [12](#support-closing-considerations-1)](#support-closing-considerations-1)

[3. Authorization Roles [13](#authorization-roles)](#authorization-roles)

[4. Document Types and Document Flow [14](#document-types-and-document-flow)](#document-types-and-document-flow)

[5. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [14](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[5.1 Reports [14](#reports)](#reports)

[5.1.1 Standard Reports [14](#standard-reports)](#standard-reports)

[5.1.2 HC Requested Reports [14](#hc-requested-reports)](#hc-requested-reports)

[5.2 Interfaces [15](#interfaces)](#interfaces)

[5.3 Conversions [15](#conversions)](#conversions)

[5.4 Enhancements [15](#enhancements)](#enhancements)

[5.5 Forms [15](#forms)](#forms)

[5.6 Workflows [15](#workflows)](#workflows)

[6. Legend for Process Flow [16](#legend-for-process-flow)](#legend-for-process-flow)

**Document Version History**

+:-----------:+:-------------------------------------------------------:+:------------------:+
| **Version** | **Summary of Change**                                   | **Effective Date** |
+-------------+---------------------------------------------------------+--------------------+
| 1.0         | Create the initial version of the document.             | 08/01/2025         |
+-------------+---------------------------------------------------------+--------------------+
| 1.1         | Chapter 2.1.4, modify the description of some processes | 08/14/2025         |
|             |                                                         |                    |
|             | Chapter 5.2, add Supply and Demand Items info           |                    |
+-------------+---------------------------------------------------------+--------------------+
|             |                                                         |                    |
+-------------+---------------------------------------------------------+--------------------+

# **Guidelines**

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

# **Scenarios**

##  **FG Planning**

2.  

<!-- -->

1.  

### **Purpose**

- The forecasting of market demand for a company's products is known as demand planning in S/4HANA and results in the creation of independent requirements, or requirements independent of actual customer demand.

- Material Requirements Planning (MRP) can be scheduled as a periodic batch job or can be manually executed as needed by the planner to create supply elements for all existing demand. Each supply element (purchase requisitions) is relevant to specific delivery date. MRP creates exception messages and summarizes this information so that it can be used by the planner to identify and address potential material shortages.

### **Business Reason**

- Demand may be planned independent requirements from Demand Management (DM), typically transferred from Sales & Operations Planning (S&OP) or forecasting, an independent demand such as a sales order, a dependent requirement (i.e. a component of a PR), a safety stock target, or it can be manually created in the system (example: a material reservation).

- MRP will run periodically, as scheduled, to create supply elements for all existing demands. In general, MRP creates a supply element if the expected supply is less than the expected demand on a certain date. MRP creates exception messages and summarizes this information so that it may be used by MRP controllers to identify and address potential material shortages or overages.

- Supply is typically the available stock, expected additions to stock such as purchase requisitions and purchase orders.

### **Business Benefits**

- Detect shortages quickly

- Create purchase requisitions or scheduling lines to cover demand automatically

- Get higher accuracy of purchased quantities

- Make use of time-dependent safety stock or time-dependent days of supply definition for replenishment

- Do a hand over for the purchase requisition (optional)

- Save costs through process automation

- Detect and resolve MRP material exceptions

1.  

### **Business Process Flow**

![](media/media/image2.emf)

### **Business Process Steps**

+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Process Step | Business Role | Transaction/App                                          | Expected Results                                                                                                                                                                                                                                                                                        |
+==============+===============+==========================================================+=========================================================================================================================================================================================================================================================================================================+
| 001          | Planner       | Manage Manual Reservations                               | Planner will create reservation for trail run, etc. It is a part of demand in MRP run.                                                                                                                                                                                                                  |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 002          | Planner       | Create Sales Orders                                      | Sales order will also be raised for customer forecast demand                                                                                                                                                                                                                                            |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 003          | Planner       | ZSD010(to be developed)                                  | As part of the planning source is LT demand. The first step is to download sales data. Quantity of open sales order, delivery and Billing is inclusive.                                                                                                                                                 |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 004          | Planner       | Non-SAP                                                  | In this activity, statistics data fetched in preceding step will be loaded to EUREKA system. SIOP procedure will launched amongst the account managers and planning team.                                                                                                                               |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005A         | Planner       | Create Sales Orders                                      | In the terms of time allocation is less than or equal to 3 months duration, forecast sales orders are raised to capture those demands.                                                                                                                                                                  |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005B         | Planner       | Maintain PlRs                                            | In the terms of time allocation is greater than 3 months duration, In the next stage when SIOP procedure is complete, planner removes records of LT lines for those time allocation which larger than 3 months.                                                                                         |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005B1        | Planner       | Maintain PlRs                                            | Output from EUREKA should be entered into SAP as an update version for planning.                                                                                                                                                                                                                        |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 006          | Planner       | Schedule MRP Runs/                                       | MRP run takes place at a scheduled time as a batch job or as required depending on the trigger. An example of a trigger would be a rush order which requests rescheduling.                                                                                                                              |
|              |               |                                                          |                                                                                                                                                                                                                                                                                                         |
|              |               | Monitor Material Coverage - Net and Individual Segments  |                                                                                                                                                                                                                                                                                                         |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 007          | Planner       | Monitor Material Coverage - Net and Individual Segments/ | Once the schedule is calculated from MRP run, planner should review and detect the incompletion of maintenance or improper scheduling time. There is no fixed supply source bound to the PR if source list is not yet maintenance. Result of check will be forwarded to responsible to fix accordingly. |
|              |               |                                                          |                                                                                                                                                                                                                                                                                                         |
|              |               | Monitor Stock / Requirements List                        |                                                                                                                                                                                                                                                                                                         |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008          | Planner       | Non-SAP                                                  | In this judging box planner to review if any change incurs.                                                                                                                                                                                                                                             |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008A         | Planner       | Non-SAP                                                  | Here a judgement to see if any change is on PIR or not: If delivery date of customer purchase is exceeding 3 months which is a PIR change; or else within 3-months time fence is a forecast sales order change.                                                                                         |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008AA        | Planner       | Maintain PlRs                                            | In this step, LT line will be changed if change is involved. The fulfilled item is removed.                                                                                                                                                                                                             |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008AA1       | Procurement   | ZFI092(to be developed)                                  | Obsolescence report is executed to see the outcome.                                                                                                                                                                                                                                                     |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008B         | Planner       | Change Sales Orders                                      | Quantity in forecast sales order will be reduced with the fulfilled quantity.                                                                                                                                                                                                                           |
+--------------+---------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

### **HC Functional Requirements**

- Ability to have authorization for the MRP run.

- Ability to save the MRP output and can filtered with buyer code.

- Ability to review MRP exception messages

- MRP can be run for plants or MRP area and materials in the scope of the Planner.

- Ability of MRP run analysis.

- Planned independent requirement can be useful to put long term forecast.

- Planner needs to see trade off demands and firm demands.

### **HC Delegation Of Authority**

- N/A

### **Standard Documents / Settings** 

- N/A

### **Design Considerations / Key Assumptions**

- Planned independent requirements are used to perform Demand Management functions. A planned independent requirement contains one planned quantity and one date, or a number of planned independent requirements schedule lines, that is, one planned quantity split over time according to dates.

- Tentative schedule for a quite a long period are categorized as long term demands. They are not fully binding as customer might change them frequently based on practical request. In Home control, planned independent requirement is created when time allocation exceeds the range of three months.

- Any customer LT in the near future will be protect by using the time fence. In Home Control, time fence is set to 10 weeks. Any actual delivery date is less than 10 weeks will be carryforwards to 10 weeks above.

### **Cross Functional Integration Dependencies**

- N/A

### **Support / Closing Considerations**

- N/A

## MRP Run {#mrp-run .LS_Heading-3}

3.  

<!-- -->

2.  

### **Purpose**

- The forecasting of market demand for a company's products is known as demand planning in S/4HANA and results in the creation of independent requirements, or requirements independent of actual customer demand.

- Material Requirements Planning (MRP) can be scheduled as a periodic batch job or can be manually executed as needed by the planner to create supply elements for all existing demand. Each supply element (purchase requisitions) is relevant to specific delivery date. MRP creates exception messages and summarizes this information so that it can be used by the planner to identify and address potential material shortages.

### **Business Reason**

- Demand may be planned independent requirements from Demand Management (DM), typically transferred from Sales & Operations Planning (S&OP) or forecasting, an independent demand such as a sales order, a dependent requirement (i.e. a component of a PR), a safety stock target, or it can be manually created in the system (example: a material reservation).

- MRP will run periodically, as scheduled, to create supply elements for all existing demands. In general, MRP creates a supply element if the expected supply is less than the expected demand on a certain date. MRP creates exception messages and summarizes this information so that it may be used by MRP controllers to identify and address potential material shortages or overages.

- Supply is typically the available stock, expected additions to stock such as purchase requisitions and purchase orders.

### **Business Benefits**

- Detect shortages quickly

- Create purchase requisitions or scheduling lines to cover demand automatically

- Get higher accuracy of purchased quantities

- Make use of time-dependent safety stock or time-dependent days of supply definition for replenishment

- Do a hand over for the purchase requisition (optional)

- Save costs through process automation

- Detect and resolve MRP material exceptions

3.  

### **Business Process Flow**

![](media/media/image3.emf)

### **Business Process Steps**

+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| Process Step | Business Role           | Transaction/App                                         | Expected Results                                                                                                                                         |
+==============+=========================+=========================================================+==========================================================================================================================================================+
| 001          | MRP Planner             | Non-SAP                                                 | Exploding from Finished planning run is one source of MRP run for raw material..                                                                         |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 002          | MRP Planner             | Manage Purchase Orders                                  | Reservation from rework request, etc is also treated as another input to MRP. For the requirement of rework, a rework purchase order is usually created. |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 003          | MRP Planner             | Create Sales Orders                                     | Another source is material sales order, from which will provide the supply to customer request, ODM or CMS scenario.                                     |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 004          | MRP Planner             | Schedule MRP Runs/                                      | The MRP run in SAP will be scheduled via a batch job.                                                                                                    |
|              |                         |                                                         |                                                                                                                                                          |
|              |                         | Monitor Material Coverage - Net and Individual Segments |                                                                                                                                                          |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005          | MRP Planner             | Non-SAP                                                 | This step describes the process of checking run generated by MRP - with the aim to download them to a report.                                            |
|              |                         |                                                         |                                                                                                                                                          |
|              |                         |                                                         | This step will be carried out by Home Control within their own system, \"Smarf fulfillment System\".                                                     |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 006          | MRP Planner             | Decision                                                | After the MRP run, validate PR Source of supply Missing?                                                                                                 |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 006A         | Purchasing /Master Data | Manage Purchasing Info Records/                         | If the PR missing source of supply, then it is necessary to check the Source List and Info Record.                                                       |
|              |                         |                                                         |                                                                                                                                                          |
|              |                         | Generate Source List                                    |                                                                                                                                                          |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 006B         | Procurement             | Non-SAP                                                 | If there is no discrepancy, procurement will download the report filtered with buyer code.                                                               |
|              |                         |                                                         |                                                                                                                                                          |
|              |                         |                                                         | This step will be carried out by Home Control within their own system, \"Smart fulfillment System\".                                                     |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008          | Procurement             | Monitor Material Coverage - Net and Individual Segments | In this step output action message to check the follow ups.                                                                                              |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
| 009          | Procurement /Purchasing | Monitor Stock / Requirements List                       | MRP run result will be reviewed by procurement /Purchasing team. Open PRs for raw material will be detected here.                                        |
+--------------+-------------------------+---------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

### **HC Functional Requirements**

- See FG Planning

### **HC Delegation Of Authority**

- N/A

### **Standard Documents / Settings** 

- N/A

### **Design Considerations / Key Assumptions**

- MRP run is schedule as batch job on daily basis. MRP planner review the outcome to ensure the validity and accuracy of the MRP run. For those errors are investigated and resolved, MRP run again either manual run or await for next batch run.

- Batch job for MRP run is scheduled on daily basis. Structure of Role setting will extend the authority to planner to provide the flexibility for manual MRP run.

- Planner and procurement need download MRP run result similar to the MDLD function in ECC. Buyer in procurement team has individual view for those materials assigned to their buyer code.

- During an MRP run, the system automatically recognizes conflict situations, and records these in the form of exception messages. The MRP controller is made aware of exceptional situations that may require attention. The procurement can view the exceptions via the 'Monitor Material Coverage - Net and Individual Segments' .

### **Cross Functional Integration Dependencies**

- N/A

### **Support / Closing Considerations**

- Regarding the function similar to MDLD in ECC, This requirement will be carried out by Home Control within their own system, \"Smart fulfillment System\".

- Some settings for the main data fields of materials:

- MRP Type: M1, M3 for finished products; PD, P1 for others

- Lot Sizing Procedure: EX for finished products; WB for others

- Procurement Type: F

- Special Procurement Type: 30, 45, 20, or blank

- Safety Time: to be maintained

- Period Indicator: default P

- Strategy Group: Z4 for kit finished products in ECC; ZN for others in ECC. The Strategy Group can no longer be custom-configured in ES, so only existing options can be selected according to the customer\'s needs. It is necessary to find another time to confirm the specific value selection of the Strategy Group with the Home Control.

- MRP Area: equivalent to setting parameters for MPR1 to MPR4 views at the MRP area level.

- All other unmentioned fields are free input fields, which should be filled in as needed and kept consistent with ECC

# Authorization Roles {#authorization-roles .LS_Heading-1}

Authorization Roles

All the roles should be divided according to the plant hierarchy.

+-------------------+------------------------------------------------------------------------------------+--------------------------------+-------------------------------------+
| **Business Role** | **Role Description**                                                               | **Authorization Restrictions** | **Baseline ZRS Role(s)**            |
+===================+====================================================================================+================================+=====================================+
| Planner           | Responsible for:                                                                   | Std Roles                      | - Z_SAP_BR_MATL_PLNR_EXT_PROC_PLANT |
|                   |                                                                                    |                                |                                     |
|                   | - Download open SO quantity, delivered quantity and billing quantity               |                                |                                     |
|                   |                                                                                    |                                |                                     |
|                   | - Upload the business data to EUREKA                                               |                                |                                     |
|                   |                                                                                    |                                |                                     |
|                   | - Manage the forecast data and make assessment on account manager' input           |                                |                                     |
|                   |                                                                                    |                                |                                     |
|                   | - Maintenance of LT line                                                           |                                |                                     |
|                   |                                                                                    |                                |                                     |
|                   | - Maintenance of forecast sales order                                              |                                |                                     |
|                   |                                                                                    |                                |                                     |
|                   | - Can run MRP manually to ensure the new change reflecting at a timely manner      |                                |                                     |
|                   |                                                                                    |                                |                                     |
|                   | - Gatekeeper of MRP run result. Analyze the result and solve before MRP finalized. |                                |                                     |
+-------------------+------------------------------------------------------------------------------------+--------------------------------+-------------------------------------+
| Procurement       | Responsible for:                                                                   | Std Roles                      | - Z_PP_MRP_RESULT_VIEW \_PLANT      |
|                   |                                                                                    |                                |                                     |
|                   | - Using exception message to analyze the outcome and resolve exception             |                                |                                     |
+-------------------+------------------------------------------------------------------------------------+--------------------------------+-------------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------
  N/A                     

  -----------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  -----------------------------------------------------------------------
  **SAP App**              **Description / Usage**
  ------------------------ ----------------------------------------------
  N/A                      

  -----------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

For details, please refer to Share Point. [Home control china\_ RIPEF Control Sheet v01](https://netorgft2607935.sharepoint.com/:x:/r/sites/HomeControlSAPCloudERPProject/_layouts/15/Doc.aspx?sourcedoc=%7BCC37AD36-6416-4148-BB9A-CA545C067C18%7D&file=Home%20control%20china_%20RIPEF%20Control%20Sheet%20v01.xlsx&action=default&mobileredirect=true)

+--------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                  |
+-----------------+-----------------+----------------+------------------+----------------+---------------------+
| **Report Name** | **Description** | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                 |                 |                |                  |                |                     |
|                 |                 |                | **SAP App/Rprt** |                |                     |
+:================+:================+:===============+:=================+:===============+:====================+
|                 |                 |                |                  |                |                     |
+-----------------+-----------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                                                                                                                                                                                                                           |
+-------------------------+-----------------------------------------------------------------------------------------------------------------------+------------------+------------------+------------------------------------------------------------------------------------------------------------------+
| **Interface**           | **Description**                                                                                                       | **In Scope**     | **Complexity**   | **Comments**                                                                                                     |
+=========================+=======================================================================================================================+:=================+:=================+:=================================================================================================================+
| Supply and Demand Items | Reads supply and demand information for materials in Material Requirements Planning (MRP) over a certain time period. | J44              |                  | API Link: [Supply and Demand Items](https://api.sap.com/api/API_MRP_MATERIALS_SRV_01/path/get_SupplyDemandItems) |
+-------------------------+-----------------------------------------------------------------------------------------------------------------------+------------------+------------------+------------------------------------------------------------------------------------------------------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

+-----------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                             |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**      | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|               |                   |                           |                            | (# items)**   |                |
+===============+===================+===========================+============================+===============+:==============:+
| N/A           |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+-----------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                    |
+------------------+------------------+------------------+------------------+-------------------------+
| **Enhancement**  | **Description**  | **Complexity**   | **In Scope**     | **Comments**            |
+==================+==================+==================+==================+:========================+
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

## Workflows {#workflows .LS_Heading-3}

The following workflows have been identified as in scope:

+---------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                             |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**      | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image4.png){width="6.6627602799650045in" height="2.4791666666666665in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems
