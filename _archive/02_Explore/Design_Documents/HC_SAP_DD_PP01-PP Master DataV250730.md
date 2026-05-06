**PP Master Data**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: PP_DD_001 PP Master Data**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Joe Wu                  PP Lead                07/30/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Yining Xu       FG Master data maintenance  

      Rocky Cai            Project Manager        

     Nancy Zhang             Supply Chain         

      Jelly Ding              Purchasing          

     Yu Xiaodong              Purchasing          

      Cherry Qu               Purchasing          

     Junfeng Shen                R&D              

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [4](#design-document-approval-options)](#design-document-approval-options)

[2. Scenarios [5](#scenarios)](#scenarios)

[2.1 Bill of Material Creation [5](#bill-of-material-creation)](#bill-of-material-creation)

[**2.1.1** **Purpose** [5](#purpose)](#purpose)

[**2.1.2** **Business Reason** [5](#business-reason)](#business-reason)

[**2.1.3** **Business Benefits** [5](#business-benefits)](#business-benefits)

[**2.1.4** **Business Process Flow** [6](#business-process-flow)](#business-process-flow)

[**2.1.5** **Business Process Steps** [6](#business-process-steps)](#business-process-steps)

[**2.1.6** **HC Functional Requirements** [7](#hc-functional-requirements)](#hc-functional-requirements)

[**2.1.7** **HC Delegation Of Authority** [7](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[**2.1.8** **Standard Documents / Settings** [7](#standard-documents-settings)](#standard-documents-settings)

[**2.1.9** **Design Considerations / Key Assumptions** [7](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[**2.1.10** **Cross Functional Integration Dependencies** [7](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[**2.1.11** **Support / Closing Considerations** [8](#support-closing-considerations)](#support-closing-considerations)

[2.2 Change Proposal with Running Change (With or Without Phase out) [8](#change-proposal-with-running-change-with-or-without-phase-out)](#change-proposal-with-running-change-with-or-without-phase-out)

[**2.2.1** **Purpose** [8](#purpose-1)](#purpose-1)

[**2.2.2** **Business Reason** [8](#business-reason-1)](#business-reason-1)

[**2.2.3** **Business Benefits** [8](#business-benefits-1)](#business-benefits-1)

[**2.2.4** **Business Process Flow** [9](#business-process-flow-1)](#business-process-flow-1)

[**2.2.5** **Business Process Steps** [9](#business-process-steps-1)](#business-process-steps-1)

[**2.2.6** **HC Functional Requirements** [10](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[**2.2.7** **HC Delegation Of Authority** [11](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[**2.2.8** **Standard Documents / Settings** [11](#standard-documents-settings-1)](#standard-documents-settings-1)

[**2.2.9** **Design Considerations / Key Assumptions** [11](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[**2.2.10** **Cross Functional Integration Dependencies** [11](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[**2.2.11** **Support / Closing Considerations** [11](#support-closing-considerations-1)](#support-closing-considerations-1)

[2.3 Change Proposal with Immediate Change [11](#change-proposal-with-immediate-change)](#change-proposal-with-immediate-change)

[**2.3.1** **Purpose** [11](#purpose-2)](#purpose-2)

[**2.3.2** **Business Reason** [11](#business-reason-2)](#business-reason-2)

[**2.2.3** **Business Benefits** [12](#business-benefits-2)](#business-benefits-2)

[**2.3.4** **Business Process Flow** [13](#business-process-flow-2)](#business-process-flow-2)

[**2.3.5** **Business Process Steps** [13](#business-process-steps-2)](#business-process-steps-2)

[**2.3.6** **HC Functional Requirements** [14](#hc-functional-requirements-2)](#hc-functional-requirements-2)

[**2.2.7** **HC Delegation Of Authority** [15](#hc-delegation-of-authority-2)](#hc-delegation-of-authority-2)

[**2.2.8** **Standard Documents / Settings** [15](#standard-documents-settings-2)](#standard-documents-settings-2)

[**2.2.9** **Design Considerations / Key Assumptions** [15](#design-considerations-key-assumptions-2)](#design-considerations-key-assumptions-2)

[**2.2.10** **Cross Functional Integration Dependencies** [15](#cross-functional-integration-dependencies-2)](#cross-functional-integration-dependencies-2)

[**2.3.11** **Support / Closing Considerations** [15](#support-closing-considerations-2)](#support-closing-considerations-2)

[3. Authorization Roles [15](#authorization-roles)](#authorization-roles)

[4. Document Types and Document Flow [16](#document-types-and-document-flow)](#document-types-and-document-flow)

[5. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [16](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[5.1 Reports [16](#reports)](#reports)

[5.1.1 Standard Reports [16](#standard-reports)](#standard-reports)

[5.1.2 HC Requested Reports [16](#hc-requested-reports)](#hc-requested-reports)

[5.2 Interfaces [16](#interfaces)](#interfaces)

[5.3 Conversions [16](#conversions)](#conversions)

[5.4 Enhancements [17](#enhancements)](#enhancements)

[5.5 Forms [17](#forms)](#forms)

[5.6 Workflows [17](#workflows)](#workflows)

[6. Legend for Process Flow [18](#legend-for-process-flow)](#legend-for-process-flow)

**Document Version History**

+:-----------:+:-------------------------------------------------------:+:------------------:+
| **Version** | **Summary of Change**                                   | **Effective Date** |
+-------------+---------------------------------------------------------+--------------------+
| 1.0         | Create the initial version of the document.             | 07/30/2025         |
+-------------+---------------------------------------------------------+--------------------+
| 1.1         | Chapter 2.1.4, modify the description of some processes | 08/14/2025         |
|             |                                                         |                    |
|             | Chapter 2.2.4, modify the description of some processes |                    |
|             |                                                         |                    |
|             | Chapter 5.2, add Bill of Material API info              |                    |
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

## **Bill of Material Creation**

2.  

<!-- -->

1.  

### **Purpose**

> A bill of materials is a formally structured list of the component materials that make up a product or assembly. The list contains the material number of each component, together with the quantity and unit of measure.
>
> BOMs are used in their different forms in various situations where a finished product or semi-finished product is manufactured from component materials.
>
> BOMs contain important basic data to support cross-functional business processes.

- MRP relevant data

- Material purchasing

- Product costing relevant data

- Consumption location data

- Scheduling related data

> Various types of BOMs can be maintained in S4/HANA.

- Material BOMs (for manufacturing)

- Engineering BOMs (for product design)

- Universal BOMs

- Plant Maintenance BOMs

- Sales and Distribution BOMs(Sales Bom)

- Predictive MRP BOMs

- Order BOM

- Service Management BOMs

This document describes the maintenance and use of manufacturing material BOMs and Sales BOMs

### **Business Reason**

The data stored in bills of material serves as a basis for planning execution activities.

- A materials planner manages product forecasting and daily MRP where material BOMs are exploded to determine cost-effective external procurement plans.

- A buyer depends on MRP to generate procurement planning with external suppliers for the BOM component materials

- The data stored in bills of material is also used in other activities in a company such as:

- Material reservations and consumption from inventory

- As an aid to data entry

- To calculate the costs of materials required for manufacturing a specific product

### **Business Benefits**

- Create and maintain single and multi-level bills of materials (BOM)

1.  

### **Business Process Flow**

![](media/media/image2.emf)

### **Business Process Steps**

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Process Step   Business Role         Transaction/App                             Expected Results
  -------------- --------------------- ------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  001            Project Team -- R&D   Non-SAP                                     The creation of a new BOM the requirement in most of the times will be generated by the Project team. R&D will be the initiator for the creation of new BOM. Procured and non-procured items will also be part of the BOM.

  002            Project Team -- R&D   Process                                     Material Master Data(HC_SAP_DD_MM01_01) this process is a pre-requisite for the BOM data creation. So the Material Master Data must have been completed before a BOM can be created.

  003            Project Team -- R&D   Non-SAP                                     R&D will fill the Excel BOM template with Header and Item data for the new BOM to be created.

  004            Purchasing            Non-SAP                                     The PPL will fill with Planning, Procurement data in the BOM template

  005            Purchasing            Non-SAP                                     PPL to coordinate and send the completed template to Master Data team.

  006            Master Data Team      Non-SAP                                     Check and verify the data provided in template. Also to check if all the materials mentioned in the BOM already exist. If the materials does not exist then the materials need to be created before uploading the BOM.

  008            Master Data Team      Custom program/ Maintain Bill of Material   There will be a BOM upload program to be created for uploading all the BOM. If the volume of data is not high then the BOM creation can be done manually directly in SAP system.

  009            Master Data Team      Maintain Bill of Material                   Check all BOM data uploaded in SAP system and verify it matches with template.

  010            Master Data Team      Non-SAP                                     Inform the project team for the completion of BOM upload in the SAP system.
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### **HC Functional Requirements**

- The key master data including material master and BOM to be created by a Master data team. The initiator for the creation of this master data will be the Project teams in most cases.

- The existing part numbers and the BOM should not change in the new SAP system. This is required as if the part numbers change then there is external dependency on the sub-contractors, stores, vendors which has a very high impact on the business. Purchase Requisitions for direct materials require approvals as defined by the D.O.A.

- There are two types of Material types which are used. One is for Finished products (FERT) and the other is semi-finished products (HALB). These are the two types of material types used in any BOM.

- The BOM of finished products is created based on base quantity equal to one pieces. If the BOM is for 1 PC finished products some of the materials may result in ratio's less than 1 unit for example corrugated boxes will be represented by 1 / 20. In those cases a special Unit of measure is required with 3 decimal places. This UOM is ZPC.

### **HC Delegation Of Authority**

- N/A

### **Standard Documents / Settings** 

- N/A

### **Design Considerations / Key Assumptions**

- The process of customizing the upload of BOM requires the definition of detailed logic and operational steps during the subsequent development phase.

### **Cross Functional Integration Dependencies**

- Product masters are to be maintained for all manufactured materials and BOM component materials

### **Support / Closing Considerations**

- There are multiple applications available in S/4HANA for creating, changing, and displaying BOMs so the user can decide which application works best for their own situation.

## Change Proposal with Running Change (With or Without Phase out) {#change-proposal-with-running-change-with-or-without-phase-out .LS_Heading-3}

3.  

<!-- -->

2.  

### **Purpose**

- Running Change: - In case of running change the stocks of the old parts are consumed before change to new part. Stocks need to be monitored for the old part and if there are stock's on the effective date then the date is adjusted in order to consume the stocks.

- Up-Point : Based on the Change Proposal one material is replaced by another in BOM. This can happen due to design changes. There can be two scenario.

- Scenario 1 :-Part A is replaced in all BOM with Part B and Part A will not be used anymore. This means Part A is phased out. In this scenario all the BOM's wherever Part A was used has been replaced with Part B. Part A will not be part of any BOM in the future.

- Scenario 2 :- Part A is replaced with Part B in some of the BOM's. So Part A and Part B co-exist. Both Part A and Part B are used in BOM's so both these materials are active and continue to be used as part of the process.

### **Business Reason**

- HC needs to manage the modification process of the BOM through this procedure, and also integrate the use of ECN.

- Handle the situation where materials are \"PHASE OUT\" during the process of modifying the BOM.

### **Business Benefits**

- Create and maintain single and multi-level bills of materials (BOM)

- Use change masters to define effectivities

- Use Where-Used function to find component occurrences with mass replacement across BOMs

- Use BOM item type as placeholder for later enhancement for business objects, like document or material

- Group BOM Items to model modularization

- Plan for intended changes with the support of impact analysis on requirements

- Ensure the fulfillment of all requirements during the product-design process

- Perform mass maintenance to add, change, and delete BOM items

- Perform mass maintenance to change and delete BOM headers

3.  

### **Business Process Flow**

![](media/media/image3.emf)

### **Business Process Steps**

+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Process Step | Business Role    | Transaction/App                                                                               | Expected Results                                                                                                                                                                                    |
+==============+==================+===============================================================================================+=====================================================================================================================================================================================================+
| 001          | Requestor        | Non-SAP                                                                                       | A requestor can ask for changes in the BOM master data. Raise a CP form for a Running change. In case of Running change the components / FG are consumed first before the change is implemented.    |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 002          | Requestor        | Material where used list in BOMs                                                              | Find where this component is used in which all BOM                                                                                                                                                  |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 003          | Requestor        | Non-SAP                                                                                       | Input the replacement part in the CP form. Also the proposed validity date is mentioned in this form.                                                                                               |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 004          | Requestor        | Non-SAP                                                                                       | CP form after completion send to the CP Approval team.                                                                                                                                              |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005          | CP Approval Team | Decision                                                                                      | CP Approval team from various departments reviews the form, checks all stocks, finalizes the validity date in the CP form and provides a decision. If the CP is not approved then the process ends. |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005A         | CP Approval Team | Decision                                                                                      | Need to check if there is additional Material master to be created? If no material master need to be created then continue the process for ECN creation.                                            |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005AA        | CP Approval Team | Process                                                                                       | If the master data to be created then follow the process for master data creation.                                                                                                                  |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 006          | Master Data Team | Manage Change Masters                                                                         | If the CP is approved then the master data team creates the ECN number is SAP. This ECN number follow the external numbering will be same as the CP number.                                         |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 007          | Master Data Team | Maintain Bill Of                                                                              | Based on the CP form make changes in the BOM using the ECN / CP number created. Assign the ECN number to this change.                                                                               |
|              |                  |                                                                                               |                                                                                                                                                                                                     |
|              |                  | Material/Mass Addition of Bills of Material ltems/Mass Maintenance of Bills of Material ltems |                                                                                                                                                                                                     |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008          | Purchasing       | Decision                                                                                      | If there is going to be a phase out happening as part of this CP change?                                                                                                                            |
|              |                  |                                                                                               |                                                                                                                                                                                                     |
|              |                  |                                                                                               | Up-Point : In this case one component is replaced by another in BOM. There can be two scenario.                                                                                                     |
|              |                  |                                                                                               |                                                                                                                                                                                                     |
|              |                  |                                                                                               | •Part A is replaced in all BOM with Part B and Part A will not be used anymore. This means Part A is phased out.                                                                                    |
|              |                  |                                                                                               |                                                                                                                                                                                                     |
|              |                  |                                                                                               | •Part A is replaced with Part B in some of the BOM's. So Part A and Part B co-exist.                                                                                                                |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008A         | Purchasing       | Non-SAP                                                                                       | If the answer to 008 is Yes then the components need to be fully consumed and the stocks to be made zero.                                                                                           |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 009          | Purchasing       | Non-SAP                                                                                       | Inform master data team once the stocks become zero.                                                                                                                                                |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 010          | Master Data Team | Manage Product Master Data                                                                    | For the phase out material tick the deletion flag.                                                                                                                                                  |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 011          | Purchasing       | Manage Purchasing Info Records                                                                | Change the validity date of the Info Record                                                                                                                                                         |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 012          | Purchasing       | Manage Source Lists                                                                           | Source List validity date to be changed                                                                                                                                                             |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

### **HC Functional Requirements**

- Engineering Change Management with Engineering change number (ECN) is required to be implemented to implement the Change Proposal in SAP system. The CP will be approved manually using excel format outside SAP. Once it is approved then the ECN will be created in SAP system based on the validity date. After ECN is created the BOM will be updated with the changes defined as part of the CP. ECN will be an external numbering.

- Any mass changes to the material master or BOM will be done only by the master data team. The authorization of these mass changes will be provided to master data team only.

### **HC Delegation Of Authority**

- N/A

### **Standard Documents / Settings** 

- N/A

### **Design Considerations / Key Assumptions**

- N/A

### **Cross Functional Integration Dependencies**

- The subsequent new version of S/4HANA Cloud may support online approval for ECN. We will consider moving the approval process online at that time.

### **Support / Closing Considerations**

- There are multiple applications available in S/4HANA Cloud for creating, changing, and displaying BOMs so the user can decide which application works best for their own situation.

## **Change Proposal with Immediate Change**

4.  

<!-- -->

3.  

<!-- -->

1.  
2.  1.  
    2.  
    3.  

### **Purpose**

- In case of immediate change the stocks of the old material either to be disposed off or to be consumed by other model.

- This change is effective immediately and the stocks are not consumed before it is implemented.

### **Business Reason**

- HC needs to manage the modification process of the BOM through this procedure, and also integrate the use of ECN.

### **Business Benefits**

- Create and maintain single and multi-level bills of materials (BOM)

- Use change masters to define effectivities

- Use Where-Used function to find component occurrences with mass replacement across BOMs

- Use BOM item type as placeholder for later enhancement for business objects, like document or material

- Group BOM Items to model modularization

- Plan for intended changes with the support of impact analysis on requirements

- Ensure the fulfillment of all requirements during the product-design process

- Perform mass maintenance to add, change, and delete BOM items

- Perform mass maintenance to change and delete BOM headers

4.  

### **Business Process Flow**

![](media/media/image4.emf)

### **Business Process Steps**

+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Process Step | Business Role    | Transaction/App                                                                               | Expected Results                                                                                                                                                                                    |
+==============+==================+===============================================================================================+=====================================================================================================================================================================================================+
| 001          | Requestor        | Non-SAP                                                                                       | A requestor can ask for changes in the BOM master data. Raise a CP form for a Running change. In case of Running change the components / FG are consumed first before the change is implemented.    |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 002          | Requestor        | Material where used list in BOMs                                                              | Find where this component is used in which all BOM                                                                                                                                                  |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 003          | Requestor        | Non-SAP                                                                                       | Input the replacement part in the CP form. Also the proposed validity date is mentioned in this form.                                                                                               |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 004          | Requestor        | Non-SAP                                                                                       | CP form after completion send to the CP Approval team.                                                                                                                                              |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005          | CP Approval Team | Decision                                                                                      | CP Approval team from various departments reviews the form, checks all stocks, finalizes the validity date in the CP form and provides a decision. If the CP is not approved then the process ends. |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005A         | CP Approval Team | Decision                                                                                      | Need to check if there is additional Material master to be created? If no material master need to be created then continue the process for ECN creation.                                            |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005AA        | CP Approval Team | Process                                                                                       | If the master data to be created then follow the process for master data creation.                                                                                                                  |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 006          | Master Data Team | Manage Change Masters                                                                         | If the CP is approved then the master data team creates the ECN number is SAP. This ECN number follow the external numbering will be same as the CP number.                                         |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 007          | Master Data Team | Maintain Bill Of                                                                              | Based on the CP form make changes in the BOM using the ECN / CP number created. Assign the ECN number to this change.                                                                               |
|              |                  |                                                                                               |                                                                                                                                                                                                     |
|              |                  | Material/Mass Addition of Bills of Material ltems/Mass Maintenance of Bills of Material ltems |                                                                                                                                                                                                     |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008          | Purchasing       | Decision                                                                                      | If the stocks need to be scrapped or consumed by other models.                                                                                                                                      |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 008A         | Purchasing       | Non-SAP                                                                                       | If the answer to 008 is Yes then the components need to be scrapped and the stocks to be made zero.                                                                                                 |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 009          | Purchasing       | Non-SAP                                                                                       | Inform master data team once the stocks become zero.                                                                                                                                                |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 010          | Master Data Team | Manage Product Master Data                                                                    | For this material tick the deletion flag.                                                                                                                                                           |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 011          | Purchasing       | Manage Purchasing Info Records                                                                | Change the validity date of the Info Record                                                                                                                                                         |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 012          | Purchasing       | Manage Source Lists                                                                           | Source List validity date to be changed                                                                                                                                                             |
+--------------+------------------+-----------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

### **HC Functional Requirements**

- Engineering Change Management with Engineering change number (ECN) is required to be implemented to implement the Change Proposal in SAP system. The CP will be approved manually using excel format outside SAP. Once it is approved then the ECN will be created in SAP system based on the validity date. After ECN is created the BOM will be updated with the changes defined as part of the CP. ECN will be an external numbering.

- Any mass changes to the material master or BOM will be done only by the master data team. The authorization of these mass changes will be provided to master data team only.

### **HC Delegation Of Authority**

- N/A

### **Standard Documents / Settings** 

- N/A

### **Design Considerations / Key Assumptions**

- N/A

### **Cross Functional Integration Dependencies**

- The subsequent new version of S/4HANA Cloud may support online approval for ECN. We will consider moving the approval process online at that time.

### **Support / Closing Considerations**

- There are multiple applications available in S/4HANA Cloud for creating, changing, and displaying BOMs so the user can decide which application works best for their own situation.

# Authorization Roles {#authorization-roles .LS_Heading-1}

Authorization Roles

All the roles should be divided according to the plant hierarchy

+-----------------------------+----------------------+--------------------------------+----------------------------------------+
| **Business Role**           | **Role Description** | **Authorization Restrictions** | **Baseline ZRS Role(s)**               |
+=============================+======================+================================+========================================+
| Project Team -- R&D         |                      | Std Roles                      | - Z_PP_MASTER_DATA_View \_Plant        |
+-----------------------------+----------------------+--------------------------------+----------------------------------------+
| Purchasing/Planning/Finance |                      | Std Roles                      | - Z_PP_MASTER_DATA_View \_Plant        |
+-----------------------------+----------------------+--------------------------------+----------------------------------------+
| Master Data Team-Product    |                      | Std Roles                      | - Z_SAP_BR_PRODMASTER_SPECIALIST_Plant |
+-----------------------------+----------------------+--------------------------------+----------------------------------------+
| Requestor                   |                      | Std Roles                      | - Z_PP_MASTER_DATA_View2_Plant         |
+-----------------------------+----------------------+--------------------------------+----------------------------------------+
| CP Approval Team            |                      |                                | - Non-SAP                              |
+-----------------------------+----------------------+--------------------------------+----------------------------------------+

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

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                                                                                                                                              |
+------------------+--------------------------------------------------------------------+------------------+------------------+-----------------------------------------------------------------------------------------------+
| **Interface**    | **Description**                                                    | **In Scope**     | **Complexity**   | **Comments**                                                                                  |
+==================+====================================================================+:=================+:=================+:==============================================================================================+
| Bill of Material | Maintain bills of material using this asynchronous inbound service |                  |                  | API Link: [Bill of Material](https://api.sap.com/api/API_BILL_OF_MATERIAL_SRV_0002/resource/) |
+------------------+--------------------------------------------------------------------+------------------+------------------+-----------------------------------------------------------------------------------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

+-----------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                             |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**      | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|               |                   |                           |                            | (# items)**   |                |
+===============+===================+===========================+============================+===============+:==============:+
| BOM           | Manual            | TBD                       | TBD                        | TBD           | TBD            |
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

![](media/media/image5.png){width="6.6627602799650045in" height="2.4791666666666665in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems
