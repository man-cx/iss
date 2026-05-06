Based on the provided functional specification document, here is the complete markdown conversion:

***

# SAP Function Specification: P006-PPCA

**Document Information**

*   **Document Name:** Home Control SAP S4HC FS- P006-PPCA
*   **Version:** V14
*   **Author:** Meos Xu
*   **Date:** 2026-01-14

## Revision History

| Version | Created Date | Updated By | Remarks |
| :--- | :--- | :--- | :--- |
| V10 | 2025/11/3 | Meos | Initial Version |
| V11 | 2025/11/7 | Meos | Add some logic |
| V12 | 2025/12/12 | Meos | Adjust the Update Price field; Adjust Valid from date logic; Adjust calculation logic of Open PO. |
| V13 | 2025/12/24 | Meos | **Update Logic**: <br>1. Open POs need to be stored in the database table. <br>2. Generate a report using the data generated after Open PO updating. <br>3. Add fields. <br>4. Update POs and make changes based on the data captured at the time when the info records are updated. |
| V14 | 2026/1/14 | Meos | Format and convert the FS to a Word version |

***

## Business Background

In the current SAP S/4HANA Public Cloud system, standard transactions are available for creating and changing Purchasing Info Records (PIR). However, SAP standard does not provide a pre-posting approval mechanism to control PIR creation or price changes before data is written into master data.

Purchasing Info Records directly impact procurement prices, sourcing decisions, material status, and open Purchase Orders. Uncontrolled changes may lead to financial risk, audit findings, and operational inconsistencies.

To address this gap, a custom approval-driven solution is required. Because approval must be completed **before** PIR data is posted, standard SAP transactions cannot be used directly. Instead, PIR data must be:

1.  Collected via predefined upload templates
2.  Validated and reviewed
3.  Approved through a configurable approval matrix
4.  Executed in SAP only after approval

Since the approval process itself is fully custom-developed, **batch PIR creation and batch PIR price changes must be developed together** as part of one integrated solution. This ensures that all PIR-related changes follow the same governance, approval, and audit logic.

***

## Business Objective

### Purchasing Info Record Upload, Approval, Creation and Change

The primary objective is to implement controlled batch upload, approval, creation, and change of Purchasing Info Records in SAP via file upload.

**Upload Scenarios**
The solution supports the following scenarios:
*   Creation of new Purchasing Info Records
*   Price change of existing Purchasing Info Records

All uploaded data must pass validation and approval before being posted to SAP master data.

**Approval Matrix**
An approval matrix is required to control PIR price-related activities:
*   One-step approval for PIR creation
*   One-step approval for price decrease scenarios
*   Two-step approval for price increase scenarios

Approval steps are dynamically determined based on price direction to ensure proper authorization and cost governance.

### Product Status Control During PIR Creation

The solution ensures controlled product status management when PIRs are created:
*   Product status must be checked before PIR creation
*   Only materials with status **ZB** are allowed for PIR creation
*   After successful PIR creation, the material status is updated to **ZC**

Product status updates are **only applied during PIR creation**, not during price change.

### Open Purchase Order Price Check and Adjustment

When PIR prices are changed, the solution provides controlled processing of open Purchase Orders:
*   Fully open PO items: update price directly
*   Partially open PO items: split PO item to isolate delivered and undelivered quantities

Open PO processing is **manually triggered by the user** after PIR update.

***

## Scope

### In Scope

The following functionalities are included within the scope of this development:
*   Upload PIR data using predefined templates
*   Validation of uploaded data
*   Step-based approval workflow
*   Batch PIR creation and price change
*   Determination of final PIR valid-from date
*   Product status update during PIR creation
*   Manual triggering of Open PO processing
*   Selection and update of eligible Open PO items

### Out of Scope

*   Automatic background Open PO processing
*   Processing of POs created after PIR updating date and Valid From date.
*   Retroactive changes to fully delivered POs
*   Product status update during PIR price change
*   Approval for objects other than PIR
*   External system integration

***

## Related Systems and Modules

*   **SAP System:** SAP S/4HANA Public Cloud
*   **SAP Module:** **MM -- Materials Management**
    *   Purchasing Info Record (PIR) creation and change
    *   Open Purchase Order (PO) processing and price updates
    *   Product Status Updates
    *   Source Lists

***

## Page Overview and UI Layout

### Overall Page Overview

The PPCA program consists of **three main user operation screens**, each representing a distinct business phase in the PIR lifecycle:

1.  **PIR Upload Screen**
2.  **PIR Review and Processing Screen**
3.  **Open Purchase Order Processing Screen**

The screens are designed to be used sequentially, but each screen can also be accessed independently based on business needs. All screens follow a consistent layout design:
*   Header area for selection criteria or upload actions
*   Main table area for data display and processing
*   Action buttons aligned with the business step of the screen

### Screen 1 -- PIR Upload Screen

**Purpose**
The PIR Upload Screen is used to upload PIR-related data using predefined Excel templates. It serves as the entry point of the PPCA process.
This screen supports:
*   PIR creation requests
*   PIR price change requests

**Key Fields and Controls**

| Field / Control | Description |
| :--- | :--- |
| **Business Type** | Determines whether the uploaded file is treated as Add Price or Change Price |
| **Upload Button** | Uploads the file |
| **Download For Template** | Downloads the template |
| **Download Button** | Downloads the data uploaded |
| **Trigger Button** | Test run: uploads and triggers data validation logic<br>Post: Posts to approval |

**Result Area Fields**

| Field | Description | Comments |
| :--- | :--- | :--- |
| **Remark** | Free-text field for additional comments or internal notes | Mandatory for Material Type: ZFER, will be fill into Long-text of info record |
| **Condition Type** | Price condition type to be maintained in the PIR | Mandatory, Default value: PPR0 |
| **Purchase Org** | Purchasing organization | Mandatory, Default value: R001 |
| **Purchase Group** | Purchasing group responsible | Mandatory, will be fill into "Supplier Material/Product group" |
| **Plant** | Plant | Mandatory |
| **Material** | Material number | Mandatory |
| **Info Category** | Category of the PIR defining the procurement scenario | Mandatory |
| **Vendor** | Vendor for whom the PIR is created | Mandatory |
| **Price** | Unit price to be maintained | Mandatory |
| **Unit** | Currency | Mandatory, currency |
| **Per** | Quantity to which the price refers | Mandatory, Default: 1000 |
| **UoM** | Unit of measure corresponding to the price quantity | Mandatory, Unit of measure |
| **Valid From** | Start date | Mandatory, Date format: YYYYMMDD |
| **Valid To** | End date of validity | Mandatory, Date format: YYYYMMDD |
| **Source List FLAG** | Indicator specifying whether the vendor should be maintained in the source list | If want to maintain Source list, Set X |
| **Quotation Attachment** | Vendor quotation document supporting the PIR creation | Mandatory, Not need for Post to info record |
| **Benchmark Quotation Attachment** | Benchmark or reference quotation used for price comparison | Not need for Post to info record |
| **Justification** | Business justification explaining the reason for creating the PIR | Mandatory when Benchmark Quotation Attachment is empty |
| **Status** | Status for PPCA | |
| **Error Log** | Error log when uploading | |
| **ID Document** | PPCA ID | will be fill into Long-text of info record |

**Processing Rules**
*   Uploaded files must strictly follow the predefined template structure
*   No SAP master data is updated at this stage
*   Successfully uploaded data is stored in staging tables and awaits review

### Screen 2 -- PIR Review and Processing Screen

**Purpose**
The PIR Review and Processing Screen is the **core control screen** of the PPCA program. It is used for:
*   Reviewing uploaded PIR data
*   Submitting requests for approval
*   Performing approval actions
*   Executing PIR creation or price changes after approval
*   Generate PO

**Key Fields (Main Table)**

| Field | Description |
| :--- | :--- |
| **ID** | Internal ID |
| **Type** | Type: 001-Add Price, 002-Update Price |
| **Approval ID** | PPCA ID |
| **Remark** | Free-text field for additional comments |
| **Info Record Number** | Info Record Number need to change |
| **ConditionType** | Price condition type |
| **PurchaseOrg** | Purchasing organization |
| **PurchaseGroup** | Purchasing group |
| **Plant** | Plant |
| **Material** | Material number |
| **InfoCategory** | Category of the PIR |
| **Vendor** | Vendor |
| **Amount** | Unit price |
| **Unit** | Currency |
| **Per** | Quantity |
| **UoM** | Unit of measure |
| **Valid From** | Start date |
| **Valid To** | End date |
| **Source List FLAG** | Indicator for source list maintenance |
| **Quotation Attachment** | Vendor quotation document |
| **Benchmark Quotation Attachment** | Benchmark or reference quotation |
| **Justification** | Business justification |
| **Requester** | Requester |
| **Approval status** | Status for Approval |
| **Line Manager** | Line Manager |
| **Manager** | Manager |
| **Approved Date** | Approved Date |
| **Info Record Number** | Generated Info Record Number |
| **Source List Number** | Generated Source List Number |
| **Product Status** | Changed Product Status |
| **Interface Logs/Status** | Status and logs for Info Record, Source List, Product Status interfaces |
| **Open PO Status/Log** | Generating Open PO status and Log |

**Approval and Execution Controls**
*   Approval buttons are enabled only for assigned approvers
*   Execute PIR Update button is enabled only when: Approval status = Approved AND Execution status = Not Executed

### Screen 3 -- Open Purchase Order Processing Screen

**Purpose**
The Open Purchase Order Processing Screen is used to:
*   Identify Open Purchase Orders affected by PIR price changes
*   Allow user-controlled update of Open PO prices
*   This screen is **manually triggered** and is not automatically executed after PIR update.

**Key Fields (Open PO Table)**

| Table Level | Field | Description |
| :--- | :--- | :--- |
| **Parent** | Info Record | Purchasing Info Record number updated |
| **Parent** | PPCA Approval ID | PPCA approval request ID |
| **Parent** | PO Date | Purchase Order document date |
| **Parent** | PO Number | Purchase Order number |
| **Parent** | PO Item | Purchase Order item number |
| **Parent** | Supplier | Supplier number |
| **Parent** | Material | Material number |
| **Parent** | Plant | Plant number |
| **Parent** | PO Quantity | Original ordered quantity of the PO item |
| **Parent** | Delivered Quantity | Quantity already delivered for the PO item |
| **Parent** | Order Unit | Order unit of measure |
| **Parent** | PO Net Price | Current net price of the PO item |
| **Parent** | Currency | Currency key of the PO price |
| **Parent** | Price Unit | Price unit maintained on the PO |
| **Parent** | Order Price UoM | Order Price UoM |
| **Parent** | Info Record Net Price | Net price from the approved PIR |
| **Parent** | Skip PO Price Change | If checked, the PO price will not be updated. |
| **Parent** | Open Quantity | Default open quantity calculated (PO item quantity - delivered quantity). Read-only |
| **Parent** | Change Status | Processing status of the PO update |
| **Child** | PO Number | Updated Purchase Order number |
| **Child** | PO Item | Updated Purchase Order item number |
| **Child** | PO Quantity | Updated quantity after PO processing |
| **Child** | Order Unit | Order unit of measure |
| **Child** | PO Net Price | Updated net price applied to the PO item |
| **Child** | Currency | Currency key |
| **Child** | Price Unit | Price unit |
| **Child** | Order Price UoM | Order Price UoM |
| **Child** | PPCA ID | PPCA approval ID linked to the PO update record |

**Processing Rules**
*   Open PO scope is fixed at the time of clicking "Generate Open PO"
*   Only selected (non-skipped) PO items are updated
*   Updates are logged for audit and traceability by SAP standard function.

### Custom Tables

*   **Tax Code Table**: used for tax code determination and validation during PIR processing
*   **Approval Matrix Table**: used to control the approval steps and approval routing for PIR creation and changes
*   **Info Record and Info Record Description Table**: used to compare Purchasing Info Records and support Open Purchase Order determination logic

***

## Upload Template Description

### Upload Template for PIR Creation

**Purpose**
Used to support batch creation of new Purchasing Info Records (PIR) through file upload. Applicable only when no Purchasing Info Record exists for the given Material, Vendor, Plant, and purchasing attributes.

**Supported Scenario:** Creation of new Purchasing Info Record (PIR)

**General Rules**
*   The predefined PIR Creation Upload Template must be used without structural changes
*   Mandatory fields must be filled according to business rules
*   Each PIR creation request is subject to approval before execution

### Upload Template for PIR Price Change

**Purpose**
Used to submit price adjustment requests for existing Purchasing Info Records through file upload. This template does not support PIR creation.

**Supported Scenario:** Price change of existing Purchasing Info Record

**General Rules**
*   The corresponding Purchasing Info Record must already exist in SAP
*   The template is used only for PIR price change scenarios
*   All price change requests require approval before being applied

***

## Business Process Flow

### End-to-End Business Process Steps

1.  **Step 1 -- PIR Data Upload**: Requestor uploads template via PIR Upload Screen.
2.  **Step 2 -- System Validation and Pre-processing**: System performs backend validation (mandatory fields, formats, material status, tax code). Errors are logged; no approval triggered yet.
3.  **Step 3 -- Manual Submission for Approval**: Requestor manually submits valid records for approval.
4.  **Step 4 -- Approval Notification**: System sends email notification to assigned approver.
5.  **Step 5 -- Approval Processing**: Approver reviews and takes action (Approve/Reject).
6.  **Step 6 -- Approval Result Notification**: System sends email notification to requestor with result.
7.  **Step 7 -- Execution Confirmation by Requestor**: Requestor confirms execution in PIR Review & Processing Screen.
8.  **Step 8 -- PIR Creation or Update Execution**: System updates SAP master data based on approved data.
9.  **Step 9 -- Source List Creation (PIR Creation Only)**: System attempts to create Source List record.
10. **Step 10 -- Material Status Update (PIR Creation Only)**: If PIR and Source List creation successful, material status updates to **ZC**.
11. **Step 11 -- Manual Trigger of Open PO Processing**: User manually clicks "Generate Open PO".
12. **Step 12 -- Open PO Update and Reporting**: System updates eligible open POs and generates results.

### Business Decision Points
*   PIR Creation versus PIR Price Change
*   Price Increase versus Price Decrease
*   Approval versus Rejection
*   Totally Open Purchase Order versus Partially Open Purchase Order
*   Purchase Order selected for update versus skipped by user

***

## Business Logic Description

### Purchasing Info Record Valid From Date Logic

**Final PIR Valid From Date = the later of:**
*   The "Valid From" date provided in the uploaded Excel template
*   The system execution timestamp when the user clicks "Execute PIR Update"

### Material Status Update Logic and Conditions

**Applicability:** Only to PIR creation scenarios.
**Pre-condition Check:** Only materials with status **ZB** are allowed.
**Post-update Logic:** Status updates to **ZC** only if PIR creation AND Source List creation are successful.

### Source List Creation Logic

**Applicability:** Only to PIR creation scenarios.
**Exception Handling:** If Source List creation fails, the PIR remains created, but Material status update is not executed.

### Open Purchase Order Scope Determination Logic

**Selection Conditions:**
*   PO item is not deleted
*   PO document date is **earlier than or equal to** the final PIR Valid From date
*   Undelivered quantity is greater than zero

**Matching Rules:**
1.  PO Info Record number equals the updated PIR number AND Plant and Item Category are the same
2.  PO old Info Record description matches the updated PIR description AND Plant and Item Category are the same

### Open Purchase Order Update Logic

**Totally Open Purchase Orders:** PO item price is updated directly to the approved PIR price.
**Partially Open Purchase Orders:**
*   Original PO item: Quantity adjusted to delivered quantity; original price retained.
*   New PO item: Quantity equals remaining undelivered quantity; price updated to approved PIR price.

### Email Notification Logic

*   **Approval Notification:** Sent to approver when request enters approval node.
*   **Approval Result Notification:** Sent to requestor after process completion.
*   **Non-trigger Scenarios:** Validation failure, request not yet submitted.

***

## Exception Handling

| Scenario | Description | System Behavior |
| :--- | :--- | :--- |
| **Validation error** | Mandatory field missing | Error log returned |
| **Approval rejection** | Rejected by approver | Status set to Rejected |
| **PIR update failure** | SAP update error | Error recorded |
| **Open PO update failure** | PO locked or authorization issue | Error logged |

***

## Authorization

| Role | Authorization |
| :--- | :--- |
| **Requester** | Upload, submit, confirm |
| **Approver** | Approve / reject |

***

## Risk and Impact Analysis

| No. | Risk Description | Business Impact | Mitigation / Control |
| :--- | :--- | :--- | :--- |
| 1 | Open POs created after PIR update execution but before new PIR price Valid From date will use old price. | Price inconsistency during gap period. | Business users must carefully plan Valid From date. |
| 2 | POs received after price update but before PIR Valid From date may be posted with new price. | Goods receipt may be posted using updated price, not aligning with original agreement. | Open PO Processing Screen allows manual exclusion of PO items. |
| 3 | Open PO processing is manually triggered. | Incorrect trigger timing may lead to unintended price updates. | Manual triggering avoids automatic mass updates; requires clear procedures/training. |
| 4 | Partially delivered POs require PO item split processing. | Increases reconciliation complexity. | Standard split logic separates delivered/undelivered quantities for traceability. |
| 5 | Open POs identified based on snapshot at "Generate Open PO" click. Subsequent changes not considered. | Subsequent PO changes may not be reflected in price adjustment. | Design ensures consistency/auditability. Users can re-trigger or handle manually if needed. |