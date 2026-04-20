**Document Management System**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: PP_DD_003 Document Management System**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

         Joe Wu                  PP Lead                08/08/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

     Minhui Zheng                R&D              

      Rocky Cai            Project Manager        

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [4](#design-document-approval-options)](#design-document-approval-options)

[2. Scenarios [4](#scenarios)](#scenarios)

[2.1 Document Management [4](#document-management)](#document-management)

[**2.1.1** **Purpose** [4](#purpose)](#purpose)

[**2.1.2** **Business Reason** [5](#business-reason)](#business-reason)

[**2.1.3** **Business Benefits** [5](#business-benefits)](#business-benefits)

[**2.1.4** **Business Process Flow** [5](#business-process-flow)](#business-process-flow)

[**2.1.5** **Business Process Steps** [6](#business-process-steps)](#business-process-steps)

[**2.1.6** **HC Functional Requirements** [6](#hc-functional-requirements)](#hc-functional-requirements)

[**2.1.7** **HC Delegation Of Authority** [7](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[**2.1.8** **Standard Documents / Settings** [7](#standard-documents-settings)](#standard-documents-settings)

[**2.1.9** **Design Considerations / Key Assumptions** [7](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[**2.1.10** **Cross Functional Integration Dependencies** [8](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[**2.1.11** **Support / Closing Considerations** [8](#support-closing-considerations)](#support-closing-considerations)

[3. Authorization Roles [8](#authorization-roles)](#authorization-roles)

[4. Document Types and Document Flow [9](#document-types-and-document-flow)](#document-types-and-document-flow)

[5. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [9](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[5.1 Reports [9](#reports)](#reports)

[5.1.1 Standard Reports [9](#standard-reports)](#standard-reports)

[5.1.2 HC Requested Reports [9](#hc-requested-reports)](#hc-requested-reports)

[5.2 Interfaces [9](#interfaces)](#interfaces)

[5.3 Conversions [10](#conversions)](#conversions)

[5.4 Enhancements [10](#enhancements)](#enhancements)

[5.5 Forms [10](#forms)](#forms)

[5.6 Workflows [10](#workflows)](#workflows)

[6. Legend for Process Flow [11](#legend-for-process-flow)](#legend-for-process-flow)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       08/08/2025

                                                              

                                                              
  ------------- --------------------------------------------- --------------------

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

## **Document Management**

2.  

<!-- -->

1.  

### **Purpose**

- Use SAP DMS to standardize the management of files generated during the design process.

### **Business Reason**

- During the product engineering phase, new products are designed and developed. You design new products or product lines to take advantage of current process technology and to improve quality and reliability. Alternately, you change an existing product due to changing market or customer requirements. The result of this product phase is drawings and specifications that must be maintained through the documents created in the Document Management System. This scope item allows for creation of a Document Info Record (DIR), and the addition and maintenance of metadata and attachments to the DIR

### **Business Benefits**

- Search and maintain Document Info Records with the new Manage Documents SAP Fiori app

- Upload and download attachments without active plug-ins

- Manage versions of the document effectively

- Share additional information simply and effectively by adding URLs

- Documents can be classified

1.  

### **Business Process Flow**

![](media/media/image2.emf)

### **Business Process Steps**

+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Process Step | Business Role    | Transaction/App             | Expected Results                                                                                                                                                                                       |
+==============+==================+=============================+========================================================================================================================================================================================================+
| 001          | R&D Engineer     | Non-SAP                     | Request for new document                                                                                                                                                                               |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 002          | Master Data Team | Process                     | If the materials do not exist, then proceed with the HC_SAP_DD_MM01_01-Material Master Data.                                                                                                           |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 003          | Master Data Team | Manage Product Master Data/ | Search document info records, First, obtain the document number through the material, and then search the document info record.                                                                        |
|              |                  |                             |                                                                                                                                                                                                        |
|              |                  | Manage Documents            |                                                                                                                                                                                                        |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 004          | Master Data Team | Condition                   | Check if there are any document info record.                                                                                                                                                           |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 004B         | Master Data Team | Manage Documents            | If it does not exist, then create a new document info record.                                                                                                                                          |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 005          | Master Data Team | Manage Documents            | In the 'Object Links' tab, link the DIR to the Material Master records of all relevant parts.                                                                                                          |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 006          | Master Data Team | Manage Documents            | In the 'Originals' tab, upload document file(s) stored within terminal into the system and attach them to the DIR.                                                                                     |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 007          | Planner          | Manage Product Master Data/ | After the DIR has been created and original document file(s) attached, users will be able to view which documents are linked to each Material Master record, and open the document file for reference. |
|              |                  |                             |                                                                                                                                                                                                        |
|              |                  | Manage Documents            |                                                                                                                                                                                                        |
+--------------+------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

### **HC Functional Requirements**

- All documents to be linked to a 12NC part number and also can be linked to a finished product.

- Original document files should be prepared on the user terminal (hard copies scanned and transferred) to be uploaded into the SAP system.

- Version control of document updates has to be present through the usage of Home Control's current procedure of numerical suffixes and revision dates.

- Sheet numbers to be reflected in order to specify the type of information it contains regarding the 12NC part.

- Document files will be linked at the individual part level, instead of at BOM level. This is required as one material can be used in many BOMs. So if there are changes in the document, all of the BOMs need to be updated.

- During the NPI process, engineers from the R&D department create drawings and graphics documents which contain the specifications for production purposes. DMS has to accommodate the uploading and viewing of all file formats currently in use by Home Control; these document files exist in various file formats.

- R&D department creates sheets which refer to the various types of specification for a particular material. These are categorized according to Sheet numbers, reflected on the document naming convention. The following is a non-exhaustive list of commonly used Sheet numbers:

  -----------------------------------------------------------
   **Sheet Number**  **Document Type(not SAP)**
  ------------------ ----------------------------------------
       **062**       Data file, ODB++ job

       **110**       Drawing

       **112**       Dimensional sketch

       **120**       Mechanical parts list

       **121**       Electrical parts list

       **124**       Packaging part list

       **130**       Schematic drawing

       **132**       Part placement drawing

       **161**       Production test specification

       **166**       Label overview

       **192**       Styling specification

       **196**       Software version document

       **293**       Packaging specification

       **296**       Transport package stacking instruction

       **374**       Product release report
  -----------------------------------------------------------

- There are frequent customer requirements for changes and updates to Home Control's products. When this happens, the design and specifications of the products have to be modified; this results in updates of several documents, all of which have to be reflected in the system.

- Searching of the documents should be possible based on Material code (i.e. 12NC).

### **HC Delegation Of Authority**

- N/A

### **Standard Documents / Settings** 

- N/A

### **Design Considerations / Key Assumptions**

- Document Type

- Currently, only one configuration is required in SAP: DOC

- This document type requires only one status: 'Released'.

### **Cross Functional Integration Dependencies**

- N/A

### **Support / Closing Considerations**

- Since only one document type is set in SAP, there is no need to set permissions according to the document type.

- The document number range cannot be customized, so the SAP standard number range will be used.

- The following file formats will be defined in the SAP system; all files with these formats can be uploaded into the system and viewed by the users with the appropriate workstation applications.

  --------------------
    **File Format**
  --------------------
          .ai

          .doc

         .easm

          .exe

          .jpg

          .pdf

          .ppt

          .txt

          .xls
  --------------------

# Authorization Roles {#authorization-roles .LS_Heading-1}

1.  

2.  

3.  

<!-- -->

1.  
2.  
3.  
4.  

<!-- -->

2.  
3.  

Authorization Roles

All the roles should be divided according to the plant hierarchy.

+-------------------+------------------------------------------------------------------------------------------------------------------------------+--------------------------------+----------------------------------------+
| **Business Role** | **Role Description**                                                                                                         | **Authorization Restrictions** | **Baseline ZRS Role(s)**               |
+===================+==============================================================================================================================+================================+========================================+
| Master Data Team  | Responsible for:                                                                                                             | Std Roles                      | - Z\_DOCUMENT_MANAGEMENT\_ MAINTENANCE |
|                   |                                                                                                                              |                                |                                        |
|                   | - creating the DIRs and uploading document updates. Also for changing of documents and changing the status of the documents. |                                |                                        |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+--------------------------------+----------------------------------------+
| User              | Responsible for:                                                                                                             | Std Roles                      | - Z\_ DOCUMENT_MANAGEMENT\_ DISPLAY    |
|                   |                                                                                                                              |                                |                                        |
|                   | - Display of all released documents.                                                                                         |                                |                                        |
+-------------------+------------------------------------------------------------------------------------------------------------------------------+--------------------------------+----------------------------------------+

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

+------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                 |
+------------------+------------------+------------------+------------------+--------------------+
| **Interface**    | **Description**  | **In Scope**     | **Complexity**   | **Comments**       |
+:=================+:=================+:=================+:=================+:===================+
| N/A              |                  |                  |                  |                    |
+------------------+------------------+------------------+------------------+--------------------+

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

![](media/media/image3.png){width="6.6627602799650045in" height="2.4791666666666665in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems
