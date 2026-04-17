**MM Master Data**

**MM主数据**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_MM01_MM Master Data**

**Version 1.2**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Meos Xu                 MM Lead                07/22/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Rocky Cai            Project Manager        

      Jelly Ding              Purchasing          

     Yu Xiaodong              Purchasing          

      Cherry Qu               Purchasing          

     Xiaoqin Zhuo            Procurement          

      Lin Zhang              Procurement          

     Nancy Zhang                 SCM              

      Sylvia Zhu               Planner            

      Irene Liu                Planner            

      Enly Teng               Logistics           

      Yining Xu        Master data maintenance    

     Junfeng Shen                R&D              

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [6](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [6](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [6](#design-document-approval-options)](#design-document-approval-options)

[2. MM Master Data [6](#mm-master-data)](#mm-master-data)

[2.1 Introduction [6](#introduction)](#introduction)

[3. Scenarios [7](#scenarios)](#scenarios)

[3.1 Maintain Material Master [7](#maintain-material-master)](#maintain-material-master)

[3.1.1 Purpose [7](#purpose)](#purpose)

[3.1.2 Business Reason [7](#business-reason)](#business-reason)

[3.1.3 Business Benefits [9](#business-benefits)](#business-benefits)

[3.1.4 Business Process Flow [9](#business-process-flow)](#business-process-flow)

[3.1.5 Business Process Steps [10](#business-process-steps)](#business-process-steps)

[3.1.6 Home Control Business Requirements [12](#home-control-business-requirements)](#home-control-business-requirements)

[3.1.7 HC Delegation Of Authority [13](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.1.8 Standard Documents / Settings [13](#standard-documents-settings)](#standard-documents-settings)

[3.1.9 Design Considerations / Key Assumptions [13](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.1.10 Support / Closing Considerations [18](#support-closing-considerations)](#support-closing-considerations)

[3.1.11 Integration Dependencies [18](#integration-dependencies)](#integration-dependencies)

[3.2 Maintain Business Partner - Supplier Master [18](#maintain-business-partner---supplier-master)](#maintain-business-partner---supplier-master)

[3.2.1 Purpose [18](#purpose-1)](#purpose-1)

[3.2.2 Business Reason [18](#business-reason-1)](#business-reason-1)

[3.2.3 Business Benefits [20](#business-benefits-1)](#business-benefits-1)

[3.2.4 Business Process Flow [20](#business-process-flow-1)](#business-process-flow-1)

[3.2.5 Business Process Steps [20](#business-process-steps-1)](#business-process-steps-1)

[3.2.6 Home Control Business Requirements [21](#home-control-business-requirements-1)](#home-control-business-requirements-1)

[3.2.7 HC Delegation Of Authority [22](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[3.2.8 Standard Documents / Settings [22](#standard-documents-settings-1)](#standard-documents-settings-1)

[3.2.9 Design Considerations / Key Assumptions [22](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[3.2.10 Support / Closing Considerations [23](#support-closing-considerations-1)](#support-closing-considerations-1)

[3.2.11 Integration Dependencies [23](#integration-dependencies-1)](#integration-dependencies-1)

[3.3 Create Purchasing Info Record and Source List and Quota Arrangement [23](#create-purchasing-info-record-and-source-list-and-quota-arrangement)](#create-purchasing-info-record-and-source-list-and-quota-arrangement)

[3.3.1 Purpose [23](#purpose-2)](#purpose-2)

[3.3.2 Business Reason [24](#business-reason-2)](#business-reason-2)

[3.3.3 Business Benefits [25](#business-benefits-2)](#business-benefits-2)

[3.3.4 Business Process Flow [25](#business-process-flow-2)](#business-process-flow-2)

[3.3.5 Business Process Steps [27](#business-process-steps-2)](#business-process-steps-2)

[3.3.6 Home Control Business Requirements [28](#home-control-business-requirements-2)](#home-control-business-requirements-2)

[3.3.7 HC Delegation Of Authority [28](#hc-delegation-of-authority-2)](#hc-delegation-of-authority-2)

[3.3.8 Standard Documents / Settings [28](#standard-documents-settings-2)](#standard-documents-settings-2)

[3.3.9 Design Considerations / Key Assumptions [28](#design-considerations-key-assumptions-2)](#design-considerations-key-assumptions-2)

[3.3.10 Support / Closing Considerations [29](#support-closing-considerations-2)](#support-closing-considerations-2)

[3.3.11 Integration Dependencies [29](#integration-dependencies-2)](#integration-dependencies-2)

[4. Authorization Roles [30](#authorization-roles)](#authorization-roles)

[4.1 Key Apps [30](#key-apps)](#key-apps)

[4.2 Authorization Roles [30](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [31](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [31](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [31](#reports)](#reports)

[6.1.1 Standard Reports [31](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [32](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [32](#interfaces)](#interfaces)

[6.3 Conversions [32](#conversions)](#conversions)

[6.4 Programs [33](#programs)](#programs)

[6.5 Enhancements [33](#enhancements)](#enhancements)

[6.6 Forms [33](#forms)](#forms)

[6.7 Workflows [33](#workflows)](#workflows)

[7. Legend for Process Flow [34](#legend-for-process-flow)](#legend-for-process-flow)

> **\**

**Document Version History**

  ------------- ------------------------------------------------------------------------------------------------------------- --------------------
   **Version**                                              **Summary of Change**                                              **Effective Date**

       1.0                                       Create the initial version of the document.                                       07/22/2025

       1.1                                 Change the process of Materials master data by comments                                 08/12/2025

       1.2       Add some comments of material master and add the process of employee BP. Change the process of info record.       08/14/2025
  ------------- ------------------------------------------------------------------------------------------------------------- --------------------

> **\**

# Guidelines {#guidelines .LS_Heading-1}

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

# MM Master Data {#mm-master-data .LS_Heading-1}

1.  

## Introduction {#introduction .LS_Heading-3}

The document focuses on maintaining Master Data related to Materials Management.

# Scenarios {#scenarios .LS_Heading-1}

The document covers the following scenarios:

- Maintain M[aterial Master]{.underline}

- Maintain Business Partner -- Vendor/Supplier Master

- Maintain Purchasing Information Record

- Maintain Source List

- Maintain Quota Arrangement

2.  

## Maintain Material Master {#maintain-material-master .LS_Heading-3}

## Purpose {#purpose .LS_Heading-3}

> This process is used to create and maintain Material Master.

## Business Reason {#business-reason .LS_Heading-3}

> The Material Master contains information on all the materials that a company procures or produces, stores, and sells. It is the company\'s central source for retrieving material-specific data. This information is stored in individual Material Master records.
>
> The Material Master is used by all components in the SAP Logistics System. The integration of all material data in a single database object eliminates redundant data storage. In the SAP Logistics System, the data contained in the Material Master is required, for example, for the following functions:

- In Purchasing, for ordering

- In Inventory Management, for goods movement postings and physical inventory

- In Invoice Verification, for posting invoices

- In Sales and Distribution, for sales order processing

- In Production Planning & Control, for material requirements planning, scheduling, & work scheduling

Material master structure follows organizational structure of a company:

> ![](media/media/image2.png){width="5.260416666666667in" height="2.931998031496063in"}

## Business Benefits {#business-benefits .LS_Heading-3}

## Business Process Flow {#business-process-flow .LS_Heading-3}

## ![](media/media/image3.emf) {#section .LS_Heading-3}

## Business Process Steps  {#business-process-steps .LS_Heading-3}

+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| **Step**          | **Step Name**                                                                | **Role**         | **SAP App Name**                                         | **Expected Results**                                                                                                                       |
+===================+==============================================================================+==================+==========================================================+============================================================================================================================================+
| 001A              | Requirement for creation of FG material                                      | Project Team     | Non-SAP                                                  | FG/Mechanical parts need to apply for external material numbers in the Smart-Fulfillment System.                                           |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 002A              | Maintain Material Master with Basic Data view and classification             | Project Team     | Non-SAP                                                  | After checking in Smart-Fulfillment System, call the materials master data interface to create.                                            |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Some fields in the material need to have their default values maintained; for details, refer to the field value XML file in section 3.1.9. |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Set the status of material to ZA                                                                                                           |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 001B              | Requirement for creation of raw material                                     | R&D              | Non-SAP                                                  | The other materials type use the numbers provided internally by Smart-Fulfillment System.                                                  |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 002B              | Maintain Material Master classification and default values in Finance view   | R&D              | Non-SAP                                                  | Some of the fields will be mandatory and other optional.                                                                                   |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Some fields in the material need to have their default values maintained; for details, refer to the field value XML file in section 3.1.9. |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Set the status of material to ZA                                                                                                           |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 003               | FG or Raw material? (Decision)                                               | R&D              | Non-SAP                                                  |                                                                                                                                            |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 004               | Maintain MRP view, Finance views, Procurements views, Sales view (If 008=No) | Master Data Team | Non-SAP                                                  | After checking in Smart-Fulfillment System, call the materials master data interface to change or create.                                  |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Some fields in the material need to have their default values maintained; for details, refer to the field value XML file in section 3.1.9. |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Set the status of material to ZB                                                                                                           |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 005               | Maintain MRP view, Price, Procurements view (If Raw material)                | Purchasing       | Non-SAP                                                  | After checking in Smart-Fulfillment System, call the materials master data interface to change or create.                                  |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Some fields in the material need to have their default values maintained; for details, refer to the field value XML file in section 3.1.9. |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Set the status of material to ZB                                                                                                           |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 006               | If Kitting materials? (Decision)                                             | Purchasing       | Non-SAP                                                  |                                                                                                                                            |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 007               | Maintain Sales view (If 006=Yes)                                             | Master Data Team | Non-SAP                                                  | After checking in Smart-Fulfillment System, call the materials master data interface to change or create.                                  |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Some fields in the material need to have their default values maintained; for details, refer to the field value XML file in section 3.1.9. |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Set the status of material to ZB                                                                                                           |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 008               | If need to maintain info record? (Decision)                                  | Master Data Team | Non-SAP                                                  | If material do not need to maintain info record, set the status of material to ZN                                                          |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Some fields in the material need to have their default values maintained; for details, refer to the field value XML file in section 3.1.9. |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| HC_SAP_DD_MM01_03 | MM Purchasing Info Record and Source List (Parallel Flow)                    | Purchasing       | Non-SAP                                                  | After maintaining info record, set the status of material to ZC                                                                            |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | Some fields in the material need to have their default values maintained; for details, refer to the field value XML file in section 3.1.9. |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 009               | Check and Verify the data                                                    | Master Data Team | Non-SAP                                                  |                                                                                                                                            |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 010               | Run costing of materials                                                     | Finance          | /                                                        | Run the cost of materials                                                                                                                  |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 011               | Change the material status                                                   | Finance          | Non-SAP                                                  | Changing material status in Smart-Fulfillment System and transferring to SAP                                                               |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | After running cost,set the status of material to ZD.                                                                                       |
|                   |                                                                              |                  |                                                          |                                                                                                                                            |
|                   |                                                                              |                  |                                                          | If need to change the status, the special status ZT is also available.                                                                     |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
| 012               | Check Material data in SAP                                                   | Finance          | Manage Product Master Data/Export Master Data - Products | Check the data in SAP                                                                                                                      |
+-------------------+------------------------------------------------------------------------------+------------------+----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

## Home Control Business Requirements {#home-control-business-requirements .LS_Heading-3}

- Home Control will use the following material types:

  -------------------------------------------
  Material Type   Material type description
  --------------- ---------------------------
  ZFER            Home Control Finished Gds

  ZH01            Diode

  ZH02            Colour LED

  ZH03            IR LED / IR Receiver

  ZH04            Transistor

  ZH05            Others Active Component

  ZH06            Capacitor, Tancap

  ZH07            Inductor

  ZH08            Crystal / Resonator

  ZH09            Resistor_PTC

  ZH10            Others Passive Component

  ZH11            Microcontroller (Blank)

  ZH12            Standard IC

  ZH13            Connector / Cable

  ZH14            Switch

  ZH15            Others (EM)

  ZH16            Battery

  ZH17            Chemical (Glue, Solder)

  ZH18            Collect Code_Transistor

  ZH19            Collect Code_Capacitor

  ZH20            Collect Code_Resistor

  ZH21            SG_Internal metal & dome

  ZH22            SG_Ext basic tool part

  ZH23            SG_Printed label / manual

  ZH24            SG_Packaging

  ZH25            SG_Mechanical Assy

  ZH26            SG_PWB

  ZH27            SG_Programming IC

  ZH28            SG_PWB Assy / SMD Assy

  ZH29            SG_Sketch Code

  ZH30            SZ_Internal metal & dome

  ZH31            SZ_Ext basic tool part

  ZH32            SZ_Printed label / manual

  ZH33            SZ_Packaging

  ZH34            SZ_Mechanical Assy

  ZH35            SZ_PWB

  ZH36            SZ_Programming IC

  ZH37            SZ_PWB Assy / SMD Assy

  ZH38            SZ_Sketch Code

  ZH39            Simand 13NC Semifinished

  ZH40            Mac Address

  ZH41            ODM Designed Parts

  ZH42            ODM Designed Parts-14NC

  ZH43            SZ_Mech Module Assy

  ZH44            Non-valuated FG

  ZHL1            Semifinish&Comp(0XXX-3XXX

  ZHL2            Semifinish&Comp(8XXX-9XXX
  -------------------------------------------

- Materials with assigned numbers exist in a legacy ERP system today. The material master data will inherit the material types, number ranges, and material numbers from the original SAP ERP.

- New material numbers created after go-live will be provided by the Smart-Fulfillment System, and the numbers in SAP ES will be externally assigned.

- Home Control will use Standard Costs for all Material Type.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Separate number range can be assigned based on Material Type.

- Material types will be assigned external number range.

  -------------------------------------------------------------------------------------
  Material Type   Material type description   From                 To
  --------------- --------------------------- -------------------- --------------------
  ZFER            Home Control Finished Gds   A                    ZZZZZZZZZZZZZZZZZZ

  ZH39            Simand 13NC Semifinished    A                    ZZZZZZZZZZZZZZZZZZ

  ZH44            Non-valuated FG             A                    ZZZZZZZZZZZZZZZZZZ

  ZHL1            Semifinish&Comp(0XXX-3XXX   000000000000000000   000000399999999999

  ZHL2            Semifinish&Comp(8XXX-9XXX   000000800000000000   000000999999999999

  ZH01            Diode                       000000501010000000   000000501010099999

  ZH02            Colour LED                  000000501020000000   000000501020099999

  ZH03            IR LED / IR Receiver        000000501030000000   000000501030099999

  ZH04            Transistor                  000000501040000000   000000501040099999

  ZH05            Others Active Component     000000501090000000   000000501090099999

  ZH06            Capacitor, Tancap           000000502010000000   000000502010099999

  ZH07            Inductor                    000000502020000000   000000502020099999

  ZH08            Crystal / Resonator         000000502030000000   000000502030099999

  ZH09            Resistor_PTC                000000502040000000   000000502040099999

  ZH10            Others Passive Component    000000502090000000   000000502090099999

  ZH11            Microcontroller (Blank)     000000503010000000   000000503010099999

  ZH12            Standard IC                 000000504010000000   000000504010099999

  ZH13            Connector / Cable           000000505010000000   000000505010099999

  ZH14            Switch                      000000505020000000   000000505020099999

  ZH15            Others (EM)                 000000505090000000   000000505090099999

  ZH16            Battery                     000000506010000000   000000506010099999

  ZH17            Chemical (Glue, Solder)     000000509010000000   000000509010099999

  ZH18            Collect Code_Transistor     000000555510000000   000000555510099999

  ZH19            Collect Code_Capacitor      000000555520000000   000000555520099999

  ZH20            Collect Code_Resistor       000000555530000000   000000555530099999

  ZH21            SG_Internal metal & dome    000000601000000000   000000601000099999

  ZH22            SG_Ext basic tool part      000000602000000000   000000602000099999

  ZH23            SG_Printed label / manual   000000603000000000   000000603000099999

  ZH24            SG_Packaging                000000604000000000   000000604000099999

  ZH25            SG_Mechanical Assy          000000605000000000   000000605000099999

  ZH26            SG_PWB                      000000606000000000   000000606000099999

  ZH27            SG_Programming IC           000000607000000000   000000607000099999

  ZH28            SG_PWB Assy / SMD Assy      000000608000000000   000000608000099999

  ZH29            SG_Sketch Code              000000723932900000   000000723932900001

  ZH30            SZ_Internal metal & dome    000000661000000001   000000661099999999

  ZH31            SZ_Ext basic tool part      000000662000000001   000000662099999999

  ZH32            SZ_Printed label / manual   000000663000000001   000000663099999999

  ZH33            SZ_Packaging                000000664000000001   000000664099999999

  ZH34            SZ_Mechanical Assy          000000665000000001   000000665099999999

  ZH35            SZ_PWB                      000000666000000001   000000666099999999

  ZH36            SZ_Programming IC           000000667000000001   000000667099999999

  ZH37            SZ_PWB Assy / SMD Assy      000000668000000001   000000668099999999

  ZH38            SZ_Sketch Code              000000723933900000   000000723933999999

  ZH40            Mac Address                 000000508010000000   000000508010099999

  ZH41            ODM Designed Parts          000000400010000000   000000400010099999

  ZH43            SZ_Mech Module Assy         000000669000000001   000000669099999999

  ZH42            ODM Designed Parts-14NC     000030000000000000   000030999999999999
  -------------------------------------------------------------------------------------

- Material number length will be limited to 18 characters

- Material Description Length is limited to 40 characters

- Valuation classes which represent inventory accounts are assigned to materials to segregate inventory by material type. The below Valuation classes will be assigned to material types:

  ---------------------------------------------------------------
  Material Type   Valuation Class   Description
  --------------- ----------------- -----------------------------
  ZFER            1106              Comm.inv. FERT (OVH Subc)

  ZH01            1006              Prod inv SEMI (OVH Subc.)

  ZH02            1006              Prod inv SEMI (OVH Subc.)

  ZH03            1006              Prod inv SEMI (OVH Subc.)

  ZH04            1006              Prod inv SEMI (OVH Subc.)

  ZH05            1006              Prod inv SEMI (OVH Subc.)

  ZH06            1006              Prod inv SEMI (OVH Subc.)

  ZH07            1006              Prod inv SEMI (OVH Subc.)

  ZH08            1006              Prod inv SEMI (OVH Subc.)

  ZH09            1006              Prod inv SEMI (OVH Subc.)

  ZH10            1006              Prod inv SEMI (OVH Subc.)

  ZH11            1006              Prod inv SEMI (OVH Subc.)

  ZH12            1006              Prod inv SEMI (OVH Subc.)

  ZH13            1006              Prod inv SEMI (OVH Subc.)

  ZH14            1006              Prod inv SEMI (OVH Subc.)

  ZH15            1006              Prod inv SEMI (OVH Subc.)

  ZH16            1006              Prod inv SEMI (OVH Subc.)

  ZH17            1006              Prod inv SEMI (OVH Subc.)

  ZH18            1006              Prod inv SEMI (OVH Subc.)

  ZH19            1006              Prod inv SEMI (OVH Subc.)

  ZH20            1006              Prod inv SEMI (OVH Subc.)

  ZH21            1006              Prod inv SEMI (OVH Subc.)

  ZH22            1006              Prod inv SEMI (OVH Subc.)

  ZH23            1006              Prod inv SEMI (OVH Subc.)

  ZH24            1006              Prod inv SEMI (OVH Subc.)

  ZH25            1006              Prod inv SEMI (OVH Subc.)

  ZH26            1006              Prod inv SEMI (OVH Subc.)

  ZH27            1006              Prod inv SEMI (OVH Subc.)

  ZH28            1006              Prod inv SEMI (OVH Subc.)

  ZH29            1006              Prod inv SEMI (OVH Subc.)

  ZH30            1006              Prod inv SEMI (OVH Subc.)

  ZH31            1006              Prod inv SEMI (OVH Subc.)

  ZH32            1006              Prod inv SEMI (OVH Subc.)

  ZH33            1006              Prod inv SEMI (OVH Subc.)

  ZH34            1006              Prod inv SEMI (OVH Subc.)

  ZH35            1006              Prod inv SEMI (OVH Subc.)

  ZH36            1006              Prod inv SEMI (OVH Subc.)

  ZH37            1006              Prod inv SEMI (OVH Subc.)

  ZH38            1006              Prod inv SEMI (OVH Subc.)

  ZH39            1006              Prod inv SEMI (OVH Subc.)

  ZH40            1006              Prod inv SEMI (OVH Subc.)

  ZH41            1006              Prod inv SEMI (OVH Subc.)

  ZH42            1006              Prod inv SEMI (OVH Subc.)

  ZH43            1006              Prod inv SEMI (OVH Subc.)

  ZH44            1006              Prod inv SEMI (OVH Subc.)

  ZHL1            1006              Prod inv SEMI (OVH Subc.)

  ZHL2            1006              Prod inv SEMI (OVH Subc.)
  ---------------------------------------------------------------

- [Home Control]{.mark} will use the following Material groups: ([TBD during Realization]{.mark})

  -----------------------------------------------------------------------------------
  **No**   **Material Group Code**   **Material Group / CLOGS Code**   **Category**
  -------- ------------------------- --------------------------------- --------------
  1        F0001                     Finished Goods                    BOM

  2        N0001                     Tools & tooling rela              Non-BOM

  3        N0002                     Freight Cost                      Non-BOM

  4        N0003                     Office maintenance &              Non-BOM

  5        N0004                     Rework / Sorting                  Non-BOM

  6        N0005                     Jigs & equipment                  Non-BOM

  7        N0006                     Service fee                       Non-BOM

  8        N0007                     IT equipment & servi              Non-BOM

  9        N0008                     Callibration, repair              Non-BOM

  10       N0009                     Test & Measurement                Non-BOM

  11       N0010                     Miscellaneous (Non-B              Non-BOM

  12       N0011                     Sample                            Non-BOM

  13       N0012                     Scrapped                          Non-BOM

  14       S0001                     PWB Assy                          BOM

  15       S0002                     SMD Assy                          BOM

  16       S0003                     Chemical                          BOM

  17       S0004                     Active                            BOM

  18       S0005                     Passive                           BOM

  19       S0006                     Batteries                         BOM

  20       S0007                     Power Supply                      BOM

  21       S0008                     Speakers & Mic                    BOM

  22       S0009                     PWB                               BOM

  23       S0010                     EM                                BOM

  24       S0011                     Keymats                           BOM

  25       S0012                     Textplate                         BOM

  26       S0013                     Polydome / Metal Dome             BOM

  27       S0014                     Metals                            BOM

  28       S0015                     Packaging & Printing              BOM

  29       S0016                     Plastics                          BOM

  30       S0017                     Chip on Board (COB)               BOM

  31       S0018                     Microcontroller                   BOM

  32       S0019                     Standard IC                       BOM

  33       S0020                     RF                                BOM

  34       S0021                     Software fee                      BOM

  35       S0022                     IC Programming                    BOM

  36       S0023                     Miscellaneous (mecha              BOM

  37       S0024                     Miscellaneous (elect              BOM

  38       S0025                     Miscellaneous (EM pa              BOM

  39       S0026                     Non-molded Light Gui              BOM

  40       S0027                     Mac Address                       BOM

  41       S0028                     ODM Designed Parts                BOM

  42       S0029                     SKD Kit Assys                     BOM

  43       S0030                     SZ_Mech Module Assy               BOM
  -----------------------------------------------------------------------------------

- [Indirect Material Groups may be assigned a default GL Account for automatic population at time of Purchase Requisition and Purchase Order entry.]{.mark} ([TBD during Realization]{.mark})

  -------------------------------------------------------------------------------------------------------
  **No**   **Material Groups**   **Material Group / CLOGS Code**   **Valuation Class**   **GL Account**
  -------- --------------------- --------------------------------- --------------------- ----------------
  27       N0001                 Tools & tooling rela                                    

  28       N0002                 Freight Cost                                            

  29       N0003                 Office maintenance &                                    

  30       N0004                 Rework / Sorting                                        

  31       N0005                 Jigs & equipment                                        

  32       N0006                 Service fee                                             

  33       N0007                 IT equipment & servi                                    

  34       N0008                 Callibration, repair                                    

  35       N0009                 Test & Measurement                                      

  36       N0010                 Miscellaneous (Non-B                                    

  37       N0011                 Sample                                                  

  38       N0012                 Scrapped                                                
  -------------------------------------------------------------------------------------------------------

- Home Control will use the following External Material groups:

> ![](media/media/image4.emf)

- Material classification

  - Phase 1 will have material Classification

  - Characteristics of the material class need to be confirmed.

![](media/media/image5.png){width="3.1178149606299215in" height="2.775138888888889in"} ![](media/media/image6.png){width="3.122762467191601in" height="2.818538932633421in"}

- Home Control will use customized SAP material statuses: （A new Status ZW）

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Status**   **Description**      **Purchase**   **BOM Header**   **BOM Items**   **R/R msg.**   **Ind Reqs**   **F/cast**   **MRP msg.**   **LT**   **PO**   **Inv Mgt**   **Cost**
  ------------ -------------------- -------------- ---------------- --------------- -------------- -------------- ------------ -------------- -------- -------- ------------- ----------
  ZA           Created              B                                                              B              B            B              B                 B             B

  ZB           Pending Purchasing                                                                                                                               B             B

  ZC           Pending Costing                                                                                                                                  B             

  ZD           Released                                                                                                                                                       

  ZL           LT Line Item                                                                                                                                     B             D

  ZN           No Costing                                                                                                                                                     B

  ZT           FOC Gd Rcpt                                                                                                                                      A             

  ZW           no recommend         A              A                A               A              A              A            A              A                 A             

  ZZ           Phase-out                           B                B               B              B              B            B              B                 B             D
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- Purchasing Group will be maintained as \"buyer\" when material for repeating order.

- Product Family to be stored in Ext. Material Group in Basic Data 1 as part of the Material master. Product Family can be maintained for components while it is not a mandatory field.

- A new UOM ZPC is required to be created with decimal places in new SAP system. ZPC to be 3 decimal places.

- A custom field need to be maintained "Model" under the basic view.

- A custom field need to be maintained "Commodity Code" under the plant level.

- The fields value requirements are as follow attachment.![](media/media/image7.emf)

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- See Conversions section for details regarding material master migration (conversion) from legacy systems.

## Integration Dependencies {#integration-dependencies .LS_Heading-3}

- Configuration of valuation classes is dependent on finance configuration (general ledger).

- Some of material master data will be determined and detailed in other related design documents, for example MRP data requirements, Storage requirements, etc.

## Maintain Business Partner - Supplier Master  {#maintain-business-partner---supplier-master .LS_Heading-3}

## Purpose {#purpose-1 .LS_Heading-3}

> This section explains the procedure of maintaining a Supplier - Business Partner.

## Business Reason {#business-reason-1 .LS_Heading-3}

> The vendor master database contains information about the vendors that supply an enterprise. This information is stored in individual BP master records. A Business Partner is a critical data record within the entire purchasing, receiving and payment process. The Business Partner contains key data necessary to:

- Create purchase orders

- Receiving shipments and Process incoming materials and parts receipts

- Create manual invoices with /without 3-way match

- Generate payment documents and Vendor payment processing

- Process invoices using 3-way match (PO -- Goods receipts and Invoices). The BP master is required for all types of transaction required in the Purchase to Pay process.

- Supplier evaluation and reporting

> A Business Partner record contains the vendor's name and address, as well as data such as:

- Name, address, tax ID

- Bank data

- Payment terms and payment methods

- The currency used for ordering from the vendor

- Names of important contact persons (sales staff)

- Bank data

> Since, to the accounts department, Suppliers are generally creditors (accounts payable), the Business Partner record also contains accounting information, such as the relevant control account (reconciliation account) in the general ledger.

## Business Benefits {#business-benefits-1 .LS_Heading-3}

## Business Process Flow {#business-process-flow-1 .LS_Heading-3}

![](media/media/image8.emf)

## Business Process Steps  {#business-process-steps-1 .LS_Heading-3}

+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| **Step** | **Step Name**                                                           | **Role**             | **SAP App Name**                                                                           | **Expected Results**                 | **Comments**                                        |
+==========+=========================================================================+======================+============================================================================================+======================================+=====================================================+
| 001      | Collect all info including bank info and fill in the application form   | Requestor/           | Non-SAP                                                                                    |                                      | BOM Vendor request will come from commodity manager |
|          |                                                                         |                      |                                                                                            |                                      |                                                     |
|          |                                                                         | Commodity Manager    |                                                                                            |                                      |                                                     |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| 002      | AP validate the bank key and fill up necessary accounting data required | AP Admin             | Non-SAP                                                                                    |                                      |                                                     |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| 003      | Approved?                                                               | Financial Controller | Non-SAP                                                                                    | Approved                             |                                                     |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| 004      | Approved?                                                               | Purchasing Director  | Non-SAP                                                                                    | Approved                             |                                                     |
|          |                                                                         |                      |                                                                                            |                                      |                                                     |
|          |                                                                         | /Site Manager        |                                                                                            |                                      |                                                     |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| 005      | Approved?                                                               | Financial Controller | Non-SAP                                                                                    | Approved                             |                                                     |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| 006      | Change Supplier Master Data                                             | Master Data Team     | Maintain Business Partner/Manage Business Partner Master Data/ Manage Supplier Master Data | The supplier master data is updated. |                                                     |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| 007      | Create Supplier Master Data                                             | Master Data Team     | Maintain Business Partner/Manage Business Partner Master Data/ Manage Supplier Master Data |                                      |                                                     |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+
| 008      | Inform Requestor/Commodity Manager the change/Creation is completed     | Master Data Team     | Non-SAP                                                                                    |                                      | Creation will update with the number                |
+----------+-------------------------------------------------------------------------+----------------------+--------------------------------------------------------------------------------------------+--------------------------------------+-----------------------------------------------------+

## Home Control Business Requirements {#home-control-business-requirements-1 .LS_Heading-3}

- Home Control will use the following Business Partner Groups:

  - BOM/NPR Vendor group :

    - Code: Z001

    - Length : 7 digitals

    - Purpose: Define for all external procurement vendor who sells to BOM materials, FG, subcontracting, ODM/CMS or services / equipment (stationary, fixed asset) to Home Control. Home Control plant vendors also belong to this group.

  - Inter Company Vendor Group:

    - Code: Z002

    - Length : 4 digitals

    - Purpose: Define for all Home Control company vendor.

  - Employee Vendor group :

    - Code: ZEMP

    - Length : 5 digitals

    - Purpose: Define for all employees under Home Control.

  - One-Time Vendor group :

    - Code: ZCPD

    - Length : 3 digitals

    - Purpose: Define for one-time vendor under Home Control.

- Business Partner -- Supplier master maintenance:

  - Requests and approval for new vendors and changes to existing vendors will out of Home Control SAP system.

  - Once maintenance request is approved, master data specialist will create or update Supplier in SAP as needed.

  - Business Partners will need to be extended to valid Purchasing Organizations that may use the same vendor.

    - R001

    - R002

    - R003

  - Business Partners will need to be extended to valid Company Code that may use the same vendor.

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-1 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- While creating Business Partner, it is required to assign to a Grouping. The following Groupings will be used:

  -----------------------------------------------------------------------------------------------------
  **Grouping**   **Name**                         **Number Range**   **Number Range**         **Ext**
  -------------- -------------------------------- ------------------ ------------------------ ---------
  Z001           SBMT Controlled BOM&NPR vendor   01                 0000100000--0009999999   

  Z002           Inter Company Vendor             XX                 AAAA--ZZZZ               √

  ZCPD           One-time vendor                  03                 0000000001-0000000999    √

  ZEMP           Employee                         02                 0000010000-0000099999    
  -----------------------------------------------------------------------------------------------------

- Vendors who are customers will have the master data. The number depends on which is created earlier

- The payment terms will be configured in FICO module.

- The payment methods will be configured for company codes in FICO module.\
  Support / Closing Considerations

- See Conversions section for details regarding vendor master migration (conversion) from legacy systems.

- The employees master data will be created by Administrator (Minting) in the APP: ***Manage Workforce,*** then the Master data team need to create supplier and supplier (Finance) role of the employee.

- The old number of employees will be maintained on business partner full name when creating.

## Support / Closing Considerations {#support-closing-considerations-1 .LS_Heading-3}

- N/A

## Integration Dependencies {#integration-dependencies-1 .LS_Heading-3}

- The Business Partner record contains information relevant to both **Accounting** and **Purchasing**. Communication and adhering to the same data standards is critical.

- The purchasing data (Trade Vendor Purchasing Org partner role) pertaining to a vendor must have previously been maintained before you can order from the vendor.

- The accounting data (Trade Vendor Company Code partner role) pertaining to a vendor must have previously been maintained before you can enter the vendor\'s invoices in the system for payment.

## Create Purchasing Info Record and Source List and Quota Arrangement {#create-purchasing-info-record-and-source-list-and-quota-arrangement .LS_Heading-3}

## Purpose {#purpose-2 .LS_Heading-3}

> Purchasing Information Record is used to store information on a vendor and a material as master data at purchasing organization or plant level. This section explains the procedure of creating a vendor business scenario.
>
> Source List specifies the allowed (and disallowed) sources of a material for a certain plant within a predefined period. Each source is defined by means of a source list record.
>
> Once source list is created for a material, this material can be only bought from sources of supply (vendors) in the list. Buying from vendors not on source list is not allowed.
>
> Quota Arrangement: If a material can be obtained from various sources of supply, each individual source of supply can be allocated a quota arrangement. The quota arrangement is valid for a certain period of time and specifies exactly how the receipts are to be distributed amongst each source of supply.
>
> Decision of quota is between Commodity Manager and Purchasing Manager. The decision will distribute to admin for follow up maintenance in SAP system. It applies in creation or change.

## Business Reason {#business-reason-2 .LS_Heading-3}

> Purchasing Information Record serves as a source of information for Purchasing. It contains information on a specific material and a vendor supplying the material. For example, the vendor\'s current pricing is stored in the info record.
>
> The info record allows buyers to quickly determine:

- Which materials have been previously offered or supplied by a specific vendor

- Which vendors have offered or supplied a specific material

> The source list can serve several purposes:

- As a list approved sources of supply. A source of supply can be a vendor, a scheduling agreement, or a plant in the case of inventory transfers from other plant.

- To define a source of supply as \"fixed\". Such sources count as preferred sources over a certain period of time.

- To define a source of supply as \"blocked\" and therefore to block the external procurement of a material from specific vendors.

- To indicate which sources are relevant to MRP.

- As an aid in selecting the preferred source during the source determination process or during MRP.

## Business Benefits {#business-benefits-2 .LS_Heading-3}

## Business Process Flow {#business-process-flow-2 .LS_Heading-3}

![](media/media/image9.emf)

## Business Process Steps  {#business-process-steps-2 .LS_Heading-3}

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Step**                       **Step Name**                                       **Role**                           **Fiori App Name**                            **Expected Results**
  ------------------------------ --------------------------------------------------- ---------------------------------- --------------------------------------------- ---------------------------------------------------------------------------------------
  001                            Request Final Quotation from Vendor                 Purchasing                         Non-SAP                                       　

  002                            Indicate in the PPCA form (Create/Change) request   Purchasing                         Non-SAP                                       Check the consistency of data, including vendor and material before filling PPCA form

  003                            Submission of PPCA Form                             Purchasing                         BTP APP                                       

  004                            Is the status of material is ZB?                                                       BTP APP                                       Check the status of materials

  005                            Create or Change?                                                                      BTP APP                                       Create or change the info record

  006                            Approved?                                           Purchasing Manager                 BTP APP                                       Approval of creation or change

  007                            If need to change the price                         Purchasing Manager                 BTP APP                                       If need to change price, trigger the price changing approval

  008                            Approved?                                           Purchasing Manager                 BTP APP                                       Approval of change price

  009                            Is price rising or falling?                         Purchasing Manager                 BTP APP                                       Check if the price is rising or falling.

  010                            Approved?                                           Purchasing Manager                 BTP APP                                       Approval of rising price.

  011                            Change the price in info record                     Purchasing Admin/SE                BTP APP                                       Change the price in info record

  012                            Change Info Record fields except for the price      Purchasing Admin/SE                BTP APP/ mass change purchasing info record   Change Info Record fields except for the price

  013                            Create Info Record & Source List                    Purchasing Admin/SE                BTP APP                                       Create Info Record & Source List

  014                            Change Source List                                  Purchasing Admin/SE                Manage source lists                           Source list is updated.

  015                            Request Final Quotation from Vendor                 Commodity Manager/Purchasing Mgr   Non-SAP                                       The quota has been confirmed.

  016                            Create Quote Master Data                            Commodity Manager/Purchasing Mgr   Manage Quota Arrangements                     Quota arrangement is created.

  017                            Change Quote Master Data                            Commodity Manager/Purchasing Mgr   Manage Quota Arrangements                     Quota arrangement is updated.

  HC_SAP_DD_PP02_02_MM MRP Run   MM MRP Run (Sub - process)                                                                                                           Qutoa is considered in MRP
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Home Control Business Requirements {#home-control-business-requirements-2 .LS_Heading-3}

- Purchasing will maintain Purchasing Info Records.

- Info records will be required for all direct materials and optional for indirect expense items.

- All direct (BOM) materials will require a source list

- Purchasing will maintain source lists based on qualifications of vendors

- Purchasing Admin will maintain quota arrangement.

## HC Delegation Of Authority {#hc-delegation-of-authority-2 .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings-2 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-2 .LS_Heading-3}

- An info record can apply to the following organizational levels:

<!-- -->

- Purchasing organization -- applicable when pricing, lead times, etc. are shared between all plants within the same purchasing organization.

<!-- -->

- Plant -- required when pricing, lead times, etc. are different for each plant.

<!-- -->

- Purchasing info records will contain the key data elements, including but not limited to:

<!-- -->

- Supplier number

- Material number

- Type of info record (standard or subcontracting)

- Order unit

- The "supplier material group" field need to borrowed to maintain SE.

- Minimum order quantity

- Incoterms

- Tax indicator

- Lead time

- Price, including price validity periods and price scales

- Additional pricing conditions (discounts, surcharges, freight charges, etc.)

- PO text (PO text from info record can be adopted in the PO item and included in the PO printout).

- 

<!-- -->

- Below Procurement types in info records will be used by Home Control:

<!-- -->

- **Standard**

> A standard info record contains information for standard purchase orders.

- **Subcontracting**

> Other types of info records available in SAP (consignment, pipeline) will not be required at go-live.

- The Source list requirement field in the purchasing data of the material master record indicates whether a source list requirement exists for a material.

## Support / Closing Considerations {#support-closing-considerations-2 .LS_Heading-3}

- N/A

## Integration Dependencies {#integration-dependencies-2 .LS_Heading-3}

- Prerequisites for maintaining purchasing info records:

  - Material master is maintained (purchasing data)

  - Supplier is maintained (purchasing data)

- Purchasing info records along with contracts and scheduling agreements are prerequisites for source list creation

# Authorization Roles {#authorization-roles .LS_Heading-1}

## Key Apps {#key-apps .LS_Heading-3}

  -------------------------------------------------------------------------------------------------------------------
  **Fiori App Name**                     **APP ID**   **Purpose**
  -------------------------------------- ------------ ---------------------------------------------------------------
  Maintain Business Partner              BP           Create/Change/ Display Business Partner Record

  Display Supplier List                  F1861        Display vendor list

  Manage Business Partner                F3163        Create/Change/ Display/Copy Business Partner

  Manage Supplier Master                 F1053A       Create/Change/ Display/Copy supplier

  Manage Purchasing Info Records         F1982        Manage (list, create, change, delete) purchasing info records

  Create Info Record                     ME11         Create Purchasing Info Record (primarily for Subcontracting)

  Change Info Record                     ME12         Change Purchasing Info Record

  Display Info Record                    ME13         Display Purchasing Info Record

  Monitor Purchasing Info Record Price   F2988        Display purchasing info record price history

  Manage Source Lists                    F1859        Manage source lists

  Maintain Source List                   ME01         Maintain source list for a material

  Manage material master data            F16102       Manage material master data

  Create Material                        MM01         Create Material

  Change Material                        MM02         Change Material

  Display Material                       MM03         Display Material

  Manage Quota Arrangements              F1877        Maintain quota arrangement
  -------------------------------------------------------------------------------------------------------------------

## Authorization Roles {#authorization-roles-1 .LS_Heading-3}

  -------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Business Role**                 **Key Tasks**                                                                   **Org Level Restrictions**
  --------------------------------- ------------------------------------------------------------------------------- -------------------------------------------
  Material Master Admin             Maintain material master (create, change, mark for deletion)                    No org level restrictions in display mode

  Purchasing Admin                  Maintain purchasing info records, source lists                                  Purchasing organization

  Business Partner Supplier Admin   Maintain BP - Supplier (create, change, block for posting, mark for deletion)   Purchasing organization, company code

  Purchasing Manager                Approve purchasing info records, source lists                                   

  MM Master Data Display            Display MM master data -- materials, vendors, info records, source lists.       No org level restrictions in display mode
  -------------------------------------------------------------------------------------------------------------------------------------------------------------

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------
  N/A                     N/A

  -----------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  ----------------------------------------------------------------------------------------------------------------------
  **Fiori App**                          **Description / Usage**                                         **Scenario#**
  -------------------------------------- --------------------------------------------------------------- ---------------
  Display Supplier List                  Display vendor list                                             3.2

  Manage Business Partner                Create/Change/ Display/Copy Business Partner                    3.2

  Manage Supplier Master                 Create/Change/ Display/Copy supplier                            3.2

  Manage Purchasing Info Records         Manage (list, create, change, delete) purchasing info records   3.3

  Monitor Purchasing Info Record Price   Display purchasing info record price history                    3.3

  Manage Source Lists                    Manage source lists                                             3.3

  Manage material master data            Manage material master data                                     3.1

  Manage Quota Arrangements              Maintain quota arrangement                                      3.3

  Manage Commodity code                  Maintain commodity code                                         3.1
  ----------------------------------------------------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+-------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                                                           |
+----------------------------------------+-----------------------------------+----------------+------------------+----------------+---------------------+
| **Report Name**                        | **Description**                   | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                                        |                                   |                |                  |                |                     |
|                                        |                                   |                | **SAP App/Rprt** |                |                     |
+:=======================================+:==================================+:===============+:=================+:===============+:====================+
| Material info record LT change history | Display LT history of info record |                |                  | Medium         |                     |
+----------------------------------------+-----------------------------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+-------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                                                                        |
+-------------------------------+-----------------------------------------------+-------------------+-------------------+-------------------------------+
| **Interface**                 | **Description**                               | **In Scope**      | **Complexity**    | **Comments**                  |
+:==============================+:==============================================+:==================+:==================+:==============================+
| Material Master data          | Material Master data                          | Yes               | Medium            | With Smart-Fulfillment System |
+-------------------------------+-----------------------------------------------+-------------------+-------------------+-------------------------------+
| Commodity Code assign Product | Commodity Code assign Product                 | Yes               | Medium            | With Smart-Fulfillment System |
+-------------------------------+-----------------------------------------------+-------------------+-------------------+-------------------------------+
| Material classification       | Material classification                       | Yes               | Medium            | With Smart-Fulfillment System |
+-------------------------------+-----------------------------------------------+-------------------+-------------------+-------------------------------+
| Info record interface         | Info record interface change Purchasing group | Yes               | Medium            | With Smart-Fulfillment System |
+-------------------------------+-----------------------------------------------+-------------------+-------------------+-------------------------------+

## Conversions {#conversions .LS_Heading-3}

Business partners other than employees shall retain their original number during migration and use the system\'s internal serial numbers after migration.

Employees shall follow the original number ranges but use the system\'s internal serial numbers, and the original numbers shall be maintained in the employee\'s name or search term.

The following data conversions have been identified as in scope:

+----------------------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                                        |
+-------------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| **Data**                | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\      | **Complexity** |
|                         |                   |                           |                            | (# items)**    |                |
+=========================+===================+===========================+============================+================+================+
| Material Master         | Spreadsheet       | Medium                    | Manual                     | Hundreds       | Medium         |
+-------------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| Business Partner        |                   | Complex                   | Complex                    | \<1,200        | High           |
+-------------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| Purchasing Info Records | Manual            | Medium                    | Medium                     | None in Legacy | Medium         |
+-------------------------+-------------------+---------------------------+----------------------------+----------------+----------------+
| Source Lists            | Manual            | Minimal                   | Medium                     | None in Legacy | Low            |
+-------------------------+-------------------+---------------------------+----------------------------+----------------+----------------+

## Programs {#programs .LS_Heading-3}

The following solution programs have been identified as in scope:

+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Programs**                                                                                                                                                                                                                                |
+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+
| **Program**                                                                            | **Description**                                                                        | **Complexity**    | **In Scope**      | **Comments**      |
+========================================================================================+========================================================================================+===================+===================+:==================+
| PPCA: mass approval (send email to approver) & create& change info record& source list | PPCA: mass approval (send email to approver) & create& change info record& source list | Very High         | No                | In BTP            |
+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+-------------------+-------------------+-------------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                                                                                                                                                                     |
+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+------------------+------------------+------------------+
| **Enhancement**                           | **Description**                                                                                                                                 | **Complexity**   | **In Scope**     | **Comments**     |
+===========================================+=================================================================================================================================================+==================+==================+:=================+
| Custom fields for ZSD008-Brand/Model Name | One field use: Industry Standard Description, the other use custom field, but may cannot extend to other reports\-\-\--need to extend to ZSD335 | Small            | No               |                  |
+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+------------------+------------------+------------------+

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

+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                                                                                                       |
+--------------------------------------------------------+--------------------------------------------------------+-------------------+-------------------+-------------------+
| **Workflow**                                           | **Description**                                        | **Complexity**    | **In Scope**      | **Comments**      |
+========================================================+========================================================+===================+===================+===================+
| Purchasing Information Record and Source List maintain | Purchasing Information Record and Source List maintain | Very High         |                   | In BTP            |
+--------------------------------------------------------+--------------------------------------------------------+-------------------+-------------------+-------------------+
| Maintain Material Master Data                          | Maintain Material Master Data                          | Med               | Out of SAP        |                   |
+--------------------------------------------------------+--------------------------------------------------------+-------------------+-------------------+-------------------+

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image10.png){width="6.407970253718285in" height="2.3860312773403325in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems
