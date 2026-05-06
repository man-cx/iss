# Wave 4: Cost & Planning Data - Execution Runbook

**Document Version:** 1.0  
**Wave Name:** Wave 4 - Cost & Planning Data  
**Timing:** Post Go-Live or T-2 weeks (if needed for Day 1)  
**Duration:** 2-3 days  
**Objects Covered:** 3 data objects (CO Planning Data, Project Master & Budgets, COPA Characteristics)

---

## Document Purpose

This runbook provides step-by-step technical procedures for executing Wave 4 data migration. Wave 4 is an optional wave that can be executed post Go-Live if planning data is not critical for Day 1 operations. Use this document together with the Wave 4 Dependencies Flow Diagram for execution guidance.

---

## Table of Contents

1. [Prerequisites & Readiness](#prerequisites--readiness)
2. [Pre-Migration Activities](#pre-migration-activities)
3. [Data Object Execution Procedures](#data-object-execution-procedures)
   - [4.1 Planning Data](#41-planning-data)
     - [CO Planning Data](#co-planning-data)
     - [Project Master & Budgets](#project-master--budgets)
     - [COPA Characteristics](#copa-characteristics)
4. [Wave 4 Load Sequence](#wave-4-load-sequence)
5. [Validation & Sign-Off Checklist](#validation--sign-off-checklist)
6. [Troubleshooting Reference](#troubleshooting-reference)

---

## Prerequisites & Readiness

### Wave 3 Completion Requirements

Before starting Wave 4, verify that Wave 3 is complete and the system is stable:

- [ ] All Wave 3 objects successfully migrated (12 objects)
- [ ] Wave 3 validation checklist signed off
- [ ] System is stable and operational (if post Go-Live)
- [ ] GL balances reconciled
- [ ] Open items migrated and validated
- [ ] Inventory balances reconciled
- [ ] No critical system issues
- [ ] User acceptance testing complete (if post Go-Live)

### Wave 4 Timing Decision

Determine the appropriate timing for Wave 4:

- [ ] **Option A: Pre-Go-Live (T-2 weeks)**
  - Planning data is critical for Day 1 reporting
  - Budget control must be active from Go-Live
  - Profitability analysis needed immediately
  - Resources available before Go-Live
  
- [ ] **Option B: Post Go-Live (Week 1-2 after Go-Live)**
  - System is stable and operational
  - Users are familiar with basic transactions
  - Planning data can wait for historical reporting
  - Focus on operational stability first

**Selected Option:** [ ] Pre-Go-Live [ ] Post Go-Live

### System Readiness

- [ ] S/4HANA system available and accessible
- [ ] Migration Cockpit configured and tested
- [ ] All migration templates imported and validated
- [ ] Sufficient storage space for data files (minimum 5 GB free)
- [ ] All technical user IDs active with proper authorizations
- [ ] CO and PS modules configured and tested

### Team Readiness

- [ ] Migration team members available for wave duration
- [ ] Functional leads (FI/CO, PS) on standby for validation
- [ ] Business users available for planning data validation
- [ ] Communication channels established
- [ ] Escalation contacts confirmed

---

## Pre-Migration Activities

### Activity 1: System Configuration Validation

Verify all required configuration is complete:

**CO Configuration:**
- [ ] Controlling area HC01 is configured
- [ ] Planning versions are defined (e.g., 0 = Current Plan)
- [ ] Cost center planning is activated
- [ ] Cost element planning is activated
- [ ] Planning layouts are configured
- [ ] Planning profiles are set up

**Transaction Codes:**
- `OKEQ` - Maintain Versions
- `KP04` - Cost Center Planning Layout

**PS Configuration:**
- [ ] Project profiles are configured
- [ ] WBS element types are defined
- [ ] Project types are set up
- [ ] Budget profiles are configured
- [ ] Settlement profiles are defined

**Transaction Codes:**
- `OPSA` - Project System Configuration
- `CJ20N` - Project Builder

**COPA Configuration:**
- [ ] Operating concern is defined
- [ ] Profitability analysis is activated
- [ ] Characteristics are defined
- [ ] Value fields are configured
- [ ] Operating concern attributes are set

**Transaction Codes:**
- `KEA0` - Maintain Operating Concern
- `KEA5` - Maintain Characteristics

### Activity 2: Template Downloads & Setup

Download all required migration templates:

- [ ] Download CO_PLAN template (CO Planning Data)
- [ ] Download PS_PROJECT template (Project Master & Budgets)
- [ ] Download COPA_CHAR template (COPA Characteristics)
- [ ] Verify template versions match S/4HANA release
- [ ] Review all mandatory fields in each template
- [ ] Test template upload with sample data

**Transaction Code:** `LTMC` - Migration Cockpit

### Activity 3: Source Data Extraction from ECC

Extract planning and project data from ECC:

**CO Planning Data Extraction:**
- [ ] Extract cost center planning data for current fiscal year
- [ ] Extract profit center planning data (if applicable)
- [ ] Extract cost element planning data
- [ ] Filter for active planning version (e.g., version 0)
- [ ] Include all 7 company codes
- [ ] Export to flat file format (CSV or Excel)

**ECC Tables for CO Planning:**
- `COSP` - CO Object: Cost Totals for External Postings
- `COSS` - CO Object: Cost Totals for Internal Postings
- `COEP` - CO Object: Line Items (Period-Related)
- `CSKA` - Cost Elements (Category)

**Project Master Extraction:**
- [ ] Extract active R&D projects with remaining budget
- [ ] Extract tooling projects
- [ ] Extract WBS element master data
- [ ] Extract project budgets
- [ ] Extract project dates and milestones
- [ ] Export to flat file format

**ECC Tables for Projects:**
- `PROJ` - Project Definition
- `PRPS` - WBS Element Master Data
- `PRHI` - Project Hierarchy
- `BPJA` - Budget (Annual Values)

**COPA Data Extraction:**
- [ ] Extract COPA characteristics definitions
- [ ] Extract operating concern attributes
- [ ] Extract value field definitions
- [ ] Extract derivation rules (if applicable)
- [ ] Document COPA structure

**ECC Tables for COPA:**
- `CE1xxxx` - Profitability Segment (xxxx = Operating Concern)
- `CE4xxxx` - COPA Line Items

### Activity 4: Data Quality Assessment

Assess data quality before migration:

**CO Planning Data:**
- [ ] Verify all cost centers exist in S/4HANA (loaded in Wave 1)
- [ ] Verify all cost elements exist in S/4HANA (loaded in Wave 1)
- [ ] Check for reasonable planning amounts (no extreme outliers)
- [ ] Validate fiscal year and period data
- [ ] Check for duplicate planning records
- [ ] Verify currency codes

**Project Master:**
- [ ] Verify all WBS elements have descriptions
- [ ] Check for valid start and end dates
- [ ] Validate budget amounts are reasonable
- [ ] Verify profit center and cost center assignments exist
- [ ] Check for circular WBS hierarchies
- [ ] Validate project statuses

**COPA:**
- [ ] Verify all customer numbers exist in S/4HANA (loaded in Wave 2)
- [ ] Verify all material numbers exist in S/4HANA (loaded in Wave 2)
- [ ] Check characteristic values are valid
- [ ] Validate profitability data is complete

### Activity 5: Workspace Preparation

Set up the migration workspace:

- [ ] Create working directory structure for Wave 4 files
- [ ] Set up naming convention: `WAVE4_OBJECT_DATE_VERSION.xlsx`
- [ ] Prepare backup location for source files
- [ ] Create error log folder
- [ ] Set up validation reports folder
- [ ] Prepare reconciliation spreadsheet templates

---

## Data Object Execution Procedures

## 4.1 Planning Data

### CO Planning Data

**Object Details:**
- **Object ID:** 37
- **Source:** ECC
- **Dependencies:** Cost Centers, Profit Centers, Cost Elements (Wave 1)
- **Complexity:** Low
- **Volume:** TBD (current fiscal year only)
- **Migration Tool:** CO_PLAN template (Migration Cockpit)
- **Priority:** Low
- **Estimated Duration:** 3-4 hours

#### Data Preparation & Cleansing

**Step 1: Extract CO Planning Data from ECC**

- [ ] Extract planning data for current fiscal year only
- [ ] Include planning version 0 (or primary planning version)
- [ ] Extract cost center planning (annual and period values)
- [ ] Extract cost element planning
- [ ] Filter for controlling area HC01
- [ ] Include all periods (1-12)

**Step 2: Data Quality Checks**

- [ ] Verify all cost centers exist in S/4HANA
- [ ] Verify all cost elements exist in S/4HANA
- [ ] Check fiscal year is current year
- [ ] Validate period numbers (1-12)
- [ ] Check planning amounts are positive (or reasonable negatives)
- [ ] Verify currency codes match company code currencies
- [ ] Check for duplicate plan records (same cost center, cost element, period)
- [ ] Validate planning version is configured in S/4HANA

**Step 3: Data Cleansing Rules**

Apply these cleansing rules:

- [ ] Remove planning data for inactive cost centers
- [ ] Remove planning data for inactive cost elements
- [ ] Standardize planning version (use version 0 or primary version)
- [ ] Aggregate planning data if needed (e.g., summarize by period)
- [ ] Convert amounts to appropriate currency
- [ ] Round amounts to 2 decimal places
- [ ] Remove zero planning values (optional - improves performance)

**Step 4: Field Mapping**

Map ECC fields to S/4HANA CO Planning structure:

| ECC Field | ECC Table | S/4HANA Field | Transformation Rule |
|-----------|-----------|---------------|---------------------|
| KOKRS | COSP/COSS | Controlling Area | Must = HC01 |
| VERSN | COSP/COSS | Version | Map to S/4HANA version (0 = Current) |
| GJAHR | COSP/COSS | Fiscal Year | Current year only |
| POPER | COSP/COSS | Period | 1-12 (or 1-16 for special periods) |
| KOSTL | COSP/COSS | Cost Center | Must exist in S/4HANA |
| KSTAR | COSP/COSS | Cost Element | Must exist in S/4HANA |
| WTGBTR | COSP/COSS | Plan Amount Total | Sum of fixed + variable |
| WTFBTR | COSP/COSS | Plan Amount Fixed | Fixed portion |
| WTVBTR | COSP/COSS | Plan Amount Variable | Variable portion |
| WAERS | COSP/COSS | Currency | ISO currency code |

**Step 5: Planning Data Structure**

Understand the planning data structure:

| Planning Level | Description | Fields Required |
|----------------|-------------|-----------------|
| Annual Planning | Total plan for year | Cost Center, Cost Element, Year, Total Amount |
| Period Planning | Monthly breakdown | Cost Center, Cost Element, Year, Period, Amount |
| Statistical KF | Non-monetary plans | Cost Center, Stat KF, Year, Period, Quantity |

**Step 6: Special Handling**

- [ ] **Planning Version:** Determine if migrating multiple versions or just version 0
- [ ] **Period Distribution:** Decide if loading annual values only or period-by-period
- [ ] **Fixed vs. Variable:** Separate fixed and variable planning if used for flexible planning
- [ ] **Statistical Key Figures:** Load separately from cost planning
- [ ] **Integration:** Ensure planning data aligns with budget control if activated

#### Load Execution

**Step 1: Prepare Migration File**

- [ ] Open CO_PLAN template from Migration Cockpit
- [ ] Copy cleansed planning data into template
- [ ] Ensure all mandatory fields populated:
  - Controlling Area (HC01)
  - Cost Center
  - Cost Element
  - Fiscal Year
  - Period (if period planning)
  - Plan Amount
  - Currency
  - Version
- [ ] Organize data by cost center and cost element
- [ ] Save file as: `WAVE4_CO_PLANNING_[DATE]_V1.xlsx`
- [ ] Create backup copy

**Step 2: Load into Migration Cockpit**

- [ ] Log into S/4HANA system
- [ ] Execute transaction `LTMC`
- [ ] Select migration project: "HOME_CONTROL_MIGRATION_WAVE4"
- [ ] Select migration object: "CO Planning Data" (or CO_PLAN)
- [ ] Create new migration run: `CO_PLAN_LOAD_[DATE]`
- [ ] Upload prepared Excel file
- [ ] Review field mappings

**Step 3: File Format & Key Parameters**

- [ ] File format: Excel (.xlsx) or CSV (UTF-8 encoding)
- [ ] Date format: `YYYY` for fiscal year
- [ ] Period format: Numeric (1-12)
- [ ] Amount format: Decimal with period separator, no thousand separators
- [ ] Currency format: ISO 3-letter code (USD, SGD, CNY, EUR, etc.)

**Configuration Parameters:**
- [ ] Simulation Mode: Yes (first run)
- [ ] Commit Block Size: 100 records
- [ ] Error Handling: Continue processing (log errors)
- [ ] Duplicate Check: Enabled
- [ ] Update Mode: Create new records only

**Step 4: Execute Load**

- [ ] Click "Start Data Import" button
- [ ] Monitor import progress in real-time
- [ ] Review any warning or error messages immediately
- [ ] Download migration log after completion
- [ ] Check statistics: Total records, Successful, Errors, Warnings

**Step 5: Error Resolution**

Common planning errors:
- [ ] Cost center not found - verify cost center loaded in Wave 1
- [ ] Cost element not found - verify cost element loaded in Wave 1
- [ ] Invalid period - check period number is 1-12
- [ ] Version not found - verify planning version configured (OKEQ)
- [ ] Duplicate planning record - check for multiple entries for same key
- [ ] Invalid currency - verify currency code

#### Pre-Import Validation

Perform these checks BEFORE loading into S/4HANA:

- [ ] **Record Count Check:** Count of planning records matches ECC extraction
- [ ] **Cost Center Check:** All cost centers exist in S/4HANA cost center master
- [ ] **Cost Element Check:** All cost elements exist in S/4HANA cost element master
- [ ] **Fiscal Year Check:** Fiscal year is current year
- [ ] **Period Check:** All periods are valid (1-12)
- [ ] **Amount Check:** Planning amounts are reasonable (no extreme outliers)
- [ ] **Currency Check:** All currency codes are valid
- [ ] **Version Check:** Planning version is configured in S/4HANA
- [ ] **Duplicate Check:** No duplicate records (same cost center, cost element, period, version)
- [ ] **Data Format Check:** All amounts, dates, and text fields follow correct format

#### Post-Import Validation

Perform these checks AFTER loading into S/4HANA:

**Step 1: Record Count Validation**

- [ ] Count total planning records loaded in S/4HANA
- [ ] Compare to source ECC count
- [ ] Variance must be zero (100% match) or documented
- [ ] Break down by cost center and cost element

**Transaction Code:** `KP06` (Cost Center Planning Report)

**Step 2: Planning Data Completeness Check**

- [ ] Open sample cost centers in planning transaction
- [ ] Verify all planning data populated correctly:
  - Cost center
  - Cost element
  - Fiscal year and periods
  - Plan amounts (annual and period values)
  - Currency
- [ ] Check 10% sample across different cost centers
- [ ] Verify annual total equals sum of period values

**Transaction Code:** `KP06` (Cost Center Planning Report) or `KP04` (Cost Center Planning Display)

**Step 3: System Access Validation**

- [ ] Display cost center planning in KP06
- [ ] Verify planning data is accessible
- [ ] Test cost center planning reports
- [ ] Check plan vs. actual reports work correctly

**Transaction Codes:**
- `KP06` - Cost Center Planning Report
- `KP04` - Cost Center Planning Display
- `S_ALR_87013611` - Cost Center: Actual/Plan/Variance

**Step 4: Functional Testing**

- [ ] **Planning Report Test:**
  - Run cost center plan/actual comparison report
  - Verify planning data displays correctly
  - Check variance calculations (if actuals exist)
  - Test different fiscal periods
  
- [ ] **Budget Control Test (if activated):**
  - Post actual cost to cost center with planning
  - Verify budget availability check works
  - Test budget overrun warning/error
  
- [ ] **Planning Change Test:**
  - Change planning data via KP06
  - Verify changes are saved
  - Check planning history is maintained

**Transaction Codes:**
- `KP06` - Cost Center Planning Display/Change
- `S_ALR_87013611` - Plan/Actual Comparison
- `FB50` - Post GL Document (for budget control test)

**Step 5: Integration Validation**

- [ ] Verify planning data available in CO reports
- [ ] Check planning data in Fiori apps (if applicable)
- [ ] Test planning data in custom reports
- [ ] Validate budget control integration (if activated)

**Step 6: Reconciliation Report**

Generate and review these reports:

- [ ] Cost Center Planning Report (by cost center, cost element)
- [ ] Compare to ECC planning reports
- [ ] Reconcile total planning amounts by cost center
- [ ] Document any exclusions or adjustments

**Transaction Code:** `KP06` (Cost Center Planning Report)

**Step 7: Totals Validation**

- [ ] Calculate total planning by cost element
- [ ] Calculate total planning by cost center
- [ ] Compare totals to ECC totals
- [ ] Variance should be zero or explained

---

### Project Master & Budgets

**Object Details:**
- **Object ID:** 38
- **Source:** ECC
- **Dependencies:** WBS Elements, Cost Elements (Wave 1), Profit Centers (Wave 1)
- **Complexity:** Medium
- **Volume:** TBD (active R&D and tooling projects with remaining budget)
- **Migration Tool:** PS_PROJECT template (Migration Cockpit)
- **Priority:** Medium
- **Estimated Duration:** 4-6 hours

#### Data Preparation & Cleansing

**Step 1: Extract Project Data from ECC**

- [ ] Extract active project definitions
- [ ] Extract WBS element master data (all levels)
- [ ] Extract project hierarchies
- [ ] Extract project budgets (annual values)
- [ ] Extract project dates (start, end, milestones)
- [ ] Filter for active R&D and tooling projects only
- [ ] Filter for projects with remaining budget
- [ ] Export to flat file format

**Step 2: Data Quality Checks**

- [ ] Verify all WBS elements have descriptions
- [ ] Check WBS element numbering is unique
- [ ] Validate project hierarchy structure (no orphans)
- [ ] Check start dates are before end dates
- [ ] Verify budget amounts are positive
- [ ] Check profit center assignments exist in S/4HANA
- [ ] Verify cost center assignments exist (if used)
- [ ] Check company code assignments are valid
- [ ] Validate project status codes
- [ ] Check for circular hierarchies

**Step 3: Data Cleansing Rules**

Apply these cleansing rules:

- [ ] Remove inactive projects (no remaining budget, closed status)
- [ ] Standardize WBS element descriptions
- [ ] Update profit center assignments to match S/4HANA
- [ ] Update cost center assignments to match S/4HANA
- [ ] Validate project dates (extend end dates if needed)
- [ ] Remove completed milestones (or mark historical)
- [ ] Clean up WBS hierarchy structure
- [ ] Update project manager assignments

**Step 4: Field Mapping**

Map ECC fields to S/4HANA Project Master structure:

| ECC Field | ECC Table | S/4HANA Field | Transformation Rule |
|-----------|-----------|---------------|---------------------|
| PSPNR | PROJ | Project Definition | Unique project ID |
| PSPHI | PROJ | WBS Element | WBS element number |
| POST1 | PROJ | Project Description | Copy as-is |
| PBUKR | PROJ | Company Code | Must be valid (SG21, CN13, etc.) |
| PRCTR | PROJ | Profit Center | Must exist in S/4HANA |
| KOSTL | PROJ | Cost Center | Must exist in S/4HANA (if used) |
| VERNR | PROJ | Responsible Person | Map to user ID |
| PLFAZ | PROJ | Start Date | YYYY-MM-DD |
| PLSEZ | PROJ | End Date | YYYY-MM-DD |
| STUFE | PRPS | Level | Hierarchy level (0=top) |
| BUDGET | BPJA | Budget Amount | Annual budget value |
| WAERS | BPJA | Currency | ISO currency code |

**Step 5: WBS Hierarchy Structure**

Understand project WBS hierarchy:

| Level | Description | Example |
|-------|-------------|---------|
| Level 0 | Project Definition | P-1000 (R&D Project) |
| Level 1 | Phase | P-1000-01 (Design Phase) |
| Level 2 | Task | P-1000-01-01 (Prototype Design) |
| Level 3 | Sub-Task | P-1000-01-01-01 (CAD Modeling) |

**Step 6: Budget Structure**

Understand budget structure:

| Budget Type | Description | Load Method |
|-------------|-------------|-------------|
| Original Budget | Initial approved budget | Load with project master |
| Supplements | Budget increases | Post separately after load |
| Returns | Budget decreases | Post separately after load |
| Available Budget | Remaining to spend | Calculated automatically |

**Step 7: Special Handling**

- [ ] **WBS Hierarchy:** Load in top-down sequence (level 0 first, then level 1, etc.)
- [ ] **Project Types:** Map ECC project types to S/4HANA project types
- [ ] **Budget Control:** Determine if budget control should be active
- [ ] **Settlement Rules:** Configure settlement rules separately (not part of migration)
- [ ] **Network Activities:** Do not migrate networks (if used) - recreate in S/4HANA
- [ ] **Project Status:** Set appropriate status (REL=Released, CRTD=Created)

#### Load Execution

**Step 1: Prepare Migration File**

- [ ] Open PS_PROJECT template from Migration Cockpit
- [ ] Copy cleansed project data into template
- [ ] Organize by WBS level (level 0 first)
- [ ] Ensure all mandatory fields populated:
  - Project Definition
  - WBS Element
  - Description
  - Company Code
  - Profit Center
  - Start Date
  - End Date
  - Budget Amount
  - Currency
- [ ] Include WBS hierarchy relationships (parent-child)
- [ ] Save file as: `WAVE4_PROJECT_MASTER_[DATE]_V1.xlsx`
- [ ] Create backup copy

**Step 2: Load into Migration Cockpit**

- [ ] Execute transaction `LTMC`
- [ ] Select migration project: "HOME_CONTROL_MIGRATION_WAVE4"
- [ ] Select migration object: "Project Master" (or PS_PROJECT)
- [ ] Create new migration run: `PROJECT_LOAD_[DATE]`
- [ ] Upload prepared Excel file
- [ ] Review field mappings

**Step 3: File Format & Key Parameters**

- [ ] File format: Excel (.xlsx) or CSV (UTF-8 encoding)
- [ ] Date format: `YYYY-MM-DD`
- [ ] Amount format: Decimal with period separator
- [ ] Hierarchy: Parent-child relationships clearly defined

**Configuration Parameters:**
- [ ] Simulation Mode: Yes (first run)
- [ ] Commit Block Size: 50 records (projects are complex)
- [ ] Error Handling: Stop on critical errors
- [ ] Duplicate Check: Enabled
- [ ] Hierarchy Load: Top-down (level 0 first)

**Step 4: Execute Load**

**For Project Master:**
- [ ] Load project definitions (level 0) first
- [ ] Load WBS elements (level 1, 2, 3...) in sequence
- [ ] Click "Start Data Import"
- [ ] Monitor progress carefully
- [ ] Review messages
- [ ] Download migration log
- [ ] Check statistics by WBS level

**For Budget Upload:**
- [ ] After project master loaded, load budgets separately
- [ ] Use transaction `CJ37` (Budget Upload) or `CJ30` (Change Budget)
- [ ] Upload budget file with WBS element and budget amount
- [ ] Verify budgets posted correctly

**Step 5: Error Resolution**

Common project errors:
- [ ] Project definition already exists - use different project ID
- [ ] WBS element already exists - check for duplicates
- [ ] Profit center not found - verify profit center master
- [ ] Cost center not found - verify cost center master
- [ ] Invalid hierarchy - check parent-child relationships
- [ ] Start date after end date - correct date logic
- [ ] Budget amount invalid - check numeric format
- [ ] Company code not valid - verify company code exists

#### Pre-Import Validation

Perform these checks BEFORE loading into S/4HANA:

- [ ] **Record Count Check:** Count of projects and WBS elements matches ECC
- [ ] **Hierarchy Check:** WBS hierarchy structure is complete (no orphans)
- [ ] **Profit Center Check:** All profit centers exist in S/4HANA
- [ ] **Cost Center Check:** All cost centers exist in S/4HANA (if used)
- [ ] **Date Check:** Start dates are before end dates
- [ ] **Budget Check:** Budget amounts are positive and reasonable
- [ ] **Company Code Check:** All company codes are valid
- [ ] **Project Status Check:** Project statuses are configured in S/4HANA
- [ ] **Duplicate Check:** No duplicate project IDs or WBS element IDs
- [ ] **Data Format Check:** All dates, amounts, and text fields follow correct format

#### Post-Import Validation

Perform these checks AFTER loading into S/4HANA:

**Step 1: Record Count Validation**

- [ ] Count total projects loaded
- [ ] Count total WBS elements by level
- [ ] Compare to source ECC count
- [ ] Variance must be zero or documented

**Transaction Code:** `CJ20N` (Project Builder)

**Step 2: Project Master Completeness Check**

- [ ] Open sample projects in Project Builder
- [ ] Verify all project data populated correctly:
  - Project definition and description
  - WBS element hierarchy
  - Company code, profit center, cost center
  - Start and end dates
  - Project status
  - Budget amounts
- [ ] Check 10% sample across different project types
- [ ] Verify WBS hierarchy displays correctly

**Transaction Code:** `CJ20N` (Project Builder) or `CJ03` (Display Project)

**Step 3: Budget Validation**

- [ ] Display project budgets
- [ ] Verify budget amounts are correct
- [ ] Check budget currency
- [ ] Verify budget is allocated to correct WBS elements
- [ ] Check budget availability

**Transaction Code:** `CJ33` (Display Budget) or `S_ALR_87013558` (Project Budget Report)

**Step 4: System Access Validation**

- [ ] Create test project posting
- [ ] Verify WBS element is selectable in posting transactions
- [ ] Test project search functionality
- [ ] Verify project hierarchy navigation works

**Transaction Codes:**
- `FB50` - Post to WBS Element
- `CJ20N` - Project Builder
- `CN41` - WBS Element Search

**Step 5: Functional Testing**

- [ ] **Project Posting Test:**
  - Post actual cost to WBS element
  - Verify posting is successful
  - Check budget consumption
  - Verify availability control (if activated)
  
- [ ] **Project Reporting Test:**
  - Run project plan/actual report
  - Verify budget and actual data displays
  - Check cost breakdown by cost element
  
- [ ] **Project Change Test:**
  - Change project master data (CJ02)
  - Verify changes are saved
  - Test budget change (CJ32)

**Transaction Codes:**
- `FB50` - Post GL Document to WBS
- `CJ02` - Change Project
- `CJ32` - Change Budget
- `S_ALR_87013558` - Project Cost/Budget Report

**Step 6: Integration Validation**

- [ ] Verify project data available in PS reports
- [ ] Check project data in Fiori apps
- [ ] Test integration with CO (cost postings)
- [ ] Validate settlement configuration (separate task)

**Step 7: Reconciliation Report**

- [ ] Generate Project List in S/4HANA
- [ ] Compare to ECC Project List
- [ ] Reconcile total project budgets
- [ ] Document any exclusions or new projects

**Transaction Codes:**
- `CN43` - Project List
- `S_ALR_87013558` - Project Budget Report

**Step 8: WBS Hierarchy Validation**

- [ ] Review WBS hierarchy structure in Project Builder
- [ ] Verify all WBS elements are at correct level
- [ ] Check parent-child relationships
- [ ] Ensure no circular hierarchies
- [ ] Verify no orphan WBS elements

**Transaction Code:** `CJ20N` (Project Builder - Structure tab)

---

### COPA Characteristics

**Object Details:**
- **Object ID:** 39
- **Source:** ECC
- **Dependencies:** Customers (Wave 2), Materials (Wave 2), Organizational Units (Wave 1)
- **Complexity:** Low
- **Volume:** TBD (characteristics and value fields setup)
- **Migration Tool:** COPA_CHAR template (Migration Cockpit) or Manual Configuration
- **Priority:** Low
- **Estimated Duration:** 2-3 hours

#### Data Preparation & Cleansing

**Step 1: Extract COPA Configuration from ECC**

- [ ] Document operating concern definition
- [ ] Extract characteristics definitions
- [ ] Extract value fields definitions
- [ ] Document derivation rules
- [ ] Extract profitability segment structure
- [ ] Document COPA attributes
- [ ] Export configuration to documentation

**Note:** COPA migration typically focuses on configuration setup rather than historical data migration. Actual profitability data (CE1xxxx tables) is usually not migrated but generated post Go-Live.

**Step 2: COPA Configuration Elements**

Document these COPA elements:

| Element | Description | Source |
|---------|-------------|--------|
| Operating Concern | High-level container | ECC configuration |
| Characteristics | Dimensions for analysis | Customer, Material, Org units |
| Value Fields | Monetary/quantity fields | Revenue, COGS, Margin |
| Derivation Rules | How to populate characteristics | ECC derivation tables |
| Assessment/Distribution | Allocation rules | ECC CO-PA configuration |

**Step 3: Data Quality Checks**

- [ ] Verify all customer numbers exist in S/4HANA (loaded in Wave 2)
- [ ] Verify all material numbers exist in S/4HANA (loaded in Wave 2)
- [ ] Check profit centers exist in S/4HANA (loaded in Wave 1)
- [ ] Verify sales organizations are configured
- [ ] Check customer groups are defined
- [ ] Verify material groups are defined

**Step 4: Characteristics Mapping**

Map ECC COPA characteristics to S/4HANA:

| ECC Characteristic | Description | S/4HANA Characteristic | Data Source |
|--------------------|-------------|------------------------|-------------|
| KNDNR | Customer | Customer | Customer Master (Wave 2) |
| ARTNR | Material | Material | Material Master (Wave 2) |
| PRCTR | Profit Center | Profit Center | Profit Center Master (Wave 1) |
| KNDGR | Customer Group | Customer Group | Customer Master |
| MATKL | Material Group | Material Group | Material Master |
| VKORG | Sales Organization | Sales Org | Organizational Units |
| VTWEG | Distribution Channel | Dist Channel | Organizational Units |
| SPART | Division | Division | Organizational Units |
| BZIRK | Sales District | Sales District | Customer Master |
| KMBRANCHE | Industry | Industry Key | Customer Master |

**Step 5: Value Fields Mapping**

Map ECC COPA value fields to S/4HANA:

| ECC Value Field | Description | S/4HANA Value Field | Data Type |
|-----------------|-------------|---------------------|-----------|
| VV010 | Revenue | Revenue | Amount |
| VV020 | Cost of Goods Sold | COGS | Amount |
| VV030 | Gross Profit | Gross Margin | Amount |
| VV040 | Sales Deductions | Deductions | Amount |
| VV050 | Sales Quantity | Sales Qty | Quantity |

**Step 6: Special Handling**

- [ ] **Operating Concern:** Configure in S/4HANA before loading characteristics
- [ ] **Universal Journal:** S/4HANA uses universal journal - COPA structure may differ
- [ ] **Derivation Rules:** Reconfigure derivation in S/4HANA (cannot directly migrate)
- [ ] **Assessment:** Reconfigure assessment cycles in S/4HANA
- [ ] **Actual Data:** Do not migrate historical COPA data - generate post Go-Live
- [ ] **Plan Data:** COPA planning data can be migrated if needed (separate from characteristics)

#### Load Execution

**Step 1: COPA Configuration (Manual)**

COPA configuration is primarily manual in S/4HANA:

**Configure Operating Concern:**
- [ ] Transaction `KEA0` (Maintain Operating Concern)
- [ ] Define operating concern name (e.g., HC01)
- [ ] Set operating concern attributes
- [ ] Activate operating concern

**Define Characteristics:**
- [ ] Transaction `KEA5` (Maintain Characteristics)
- [ ] Add characteristics to operating concern:
  - Customer Number (KNDNR)
  - Material Number (ARTNR)
  - Profit Center (PRCTR)
  - Customer Group (KNDGR)
  - Material Group (MATKL)
  - Sales Organization (VKORG)
  - Distribution Channel (VTWEG)
  - Division (SPART)
  - (Add others as needed)
- [ ] Set characteristic attributes (length, data type)
- [ ] Save and generate operating concern

**Define Value Fields:**
- [ ] Transaction `KEA6` (Maintain Value Fields)
- [ ] Add value fields to operating concern:
  - VV010 (Revenue)
  - VV020 (COGS)
  - VV030 (Gross Profit)
  - VV040 (Sales Deductions)
  - VV050 (Sales Quantity)
  - (Add others as needed)
- [ ] Set value field attributes (data type, currency/unit)
- [ ] Save and generate

**Step 2: Derivation Rules Configuration**

- [ ] Transaction `KEDR` (Maintain Derivation Rules)
- [ ] Configure derivation for each characteristic:
  - Customer Group from Customer Master
  - Material Group from Material Master
  - Profit Center from Organizational Assignment
  - Sales District from Customer Master
- [ ] Define derivation table logic
- [ ] Test derivation rules
- [ ] Activate rules

**Step 3: COPA Data Flow Activation**

- [ ] Configure actual data flow from SD/MM/FI to COPA
- [ ] Set up automatic posting to profitability analysis
- [ ] Configure transfer of billing documents
- [ ] Set up assessment/distribution cycles (if used)

**Transaction Codes:**
- `KEAT` - Actual Data Flow
- `KE4R` - Transfer Billing Documents
- `KEU1` - Assessment Cycle
- `KEU5` - Distribution Cycle

**Step 4: Alternative - Template Load (if available)**

If using COPA_CHAR template:

- [ ] Prepare characteristic master data file
- [ ] Open COPA_CHAR template
- [ ] Enter characteristic definitions
- [ ] Save as: `WAVE4_COPA_CHAR_[DATE]_V1.xlsx`
- [ ] Load via Migration Cockpit
- [ ] Execute load

**Note:** Most S/4HANA implementations require manual COPA configuration rather than template load.

**Step 5: Error Resolution**

Common COPA errors:
- [ ] Operating concern not activated - activate via KEA0
- [ ] Characteristic not defined - add characteristic via KEA5
- [ ] Value field not found - define value field via KEA6
- [ ] Derivation error - check derivation rules in KEDR
- [ ] Customer/Material not found - verify master data loaded

#### Pre-Import Validation

Perform these checks BEFORE activating COPA:

- [ ] **Operating Concern Check:** Operating concern is defined and activated
- [ ] **Characteristic Check:** All required characteristics are defined
- [ ] **Value Field Check:** All required value fields are defined
- [ ] **Master Data Check:** All customers, materials, profit centers exist in S/4HANA
- [ ] **Derivation Check:** Derivation rules are configured
- [ ] **Data Flow Check:** Actual data flow is configured
- [ ] **Currency Check:** Currency fields are properly configured
- [ ] **UOM Check:** Quantity fields have proper unit of measure

#### Post-Import Validation

Perform these checks AFTER COPA configuration:

**Step 1: Configuration Validation**

- [ ] Operating concern is activated
- [ ] All characteristics are defined
- [ ] All value fields are defined
- [ ] Derivation rules are active
- [ ] Data flow is configured

**Transaction Code:** `KEA0` (Operating Concern Overview)

**Step 2: Characteristics Validation**

- [ ] Display operating concern in KEA0
- [ ] Verify all characteristics are listed
- [ ] Check characteristic attributes (length, type)
- [ ] Verify characteristic values are populated from master data

**Transaction Code:** `KEA5` (Display Characteristics)

**Step 3: Value Fields Validation**

- [ ] Display value fields in KEA6
- [ ] Verify all value fields are listed
- [ ] Check value field attributes (currency, unit)
- [ ] Verify value field data types

**Transaction Code:** `KEA6` (Display Value Fields)

**Step 4: Functional Testing**

- [ ] **COPA Posting Test:**
  - Create test sales order
  - Process billing document
  - Verify COPA line item created
  - Check characteristic values populated
  - Verify value fields calculated correctly
  
- [ ] **Derivation Test:**
  - Test derivation for customer group
  - Test derivation for material group
  - Test derivation for profit center
  - Verify all derivations work correctly
  
- [ ] **COPA Reporting Test:**
  - Run profitability report (KE30)
  - Verify data displays correctly
  - Check drill-down by characteristics
  - Test different report layouts

**Transaction Codes:**
- `VA01` - Create Sales Order (triggers COPA)
- `VF01` - Create Billing Document (posts to COPA)
- `KE24` - Display COPA Line Items
- `KE30` - Run Profitability Report

**Step 5: System Access Validation**

- [ ] COPA line items are created from billing
- [ ] COPA reports are accessible
- [ ] Characteristics can be displayed
- [ ] Drilldown functionality works

**Transaction Codes:**
- `KE24` - COPA Line Items
- `KE30` - Profitability Report
- `KE5Z` - COPA Planning

**Step 6: Integration Validation**

- [ ] Verify COPA integration with SD (billing documents)
- [ ] Check COPA integration with FI (revenue postings)
- [ ] Test COPA integration with CO (cost allocations)
- [ ] Validate characteristic derivation from master data

**Step 7: Reconciliation**

- [ ] Compare COPA configuration to ECC
- [ ] Verify all characteristics migrated
- [ ] Check all value fields migrated
- [ ] Document any configuration differences

**Step 8: Reporting Validation**

- [ ] Create sample profitability reports
- [ ] Verify report layouts work
- [ ] Check characteristic drill-down
- [ ] Test plan/actual comparisons (if planning used)

**Transaction Code:** `KE30` (Profitability Report)

---

## Wave 4 Load Sequence

Execute Wave 4 objects in the following sequence:

### Phase 1: CO Planning Data (Day 1)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 1.1 | CO Planning Data | CO_PLAN template | 3-4 hrs | Cost Centers, Cost Elements (Wave 1) | [ ] |

**Phase 1 Checkpoint:**
- [ ] Planning data loaded and validated
- [ ] Planning reports accessible
- [ ] Budget control tested (if activated)
- [ ] Reconciliation complete

### Phase 2: Project Master (Day 1-2)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 2.1 | Project Master & Budgets | PS_PROJECT template | 4-6 hrs | Profit Centers, Cost Centers, Cost Elements (Wave 1) | [ ] |

**Phase 2 Checkpoint:**
- [ ] Projects and WBS elements loaded
- [ ] WBS hierarchy validated
- [ ] Budgets uploaded and verified
- [ ] Project postings tested
- [ ] Reconciliation complete

### Phase 3: COPA Configuration (Day 2-3)

| Step | Object | Tool | Duration | Dependencies | Status |
|------|--------|------|----------|--------------|--------|
| 3.1 | COPA Characteristics | Manual Config (KEA0/KEA5/KEA6) | 2-3 hrs | Customers, Materials, Profit Centers | [ ] |

**Phase 3 Checkpoint:**
- [ ] Operating concern activated
- [ ] Characteristics configured
- [ ] Value fields configured
- [ ] Derivation rules activated
- [ ] Data flow configured
- [ ] COPA posting tested
- [ ] Reports accessible

### Phase 4: Final Validation & Sign-Off (Day 3)

| Step | Activity | Duration | Status |
|------|----------|----------|--------|
| 4.1 | End-to-end integration testing | 2 hrs | [ ] |
| 4.2 | Complete all validation checklists | 1 hr | [ ] |
| 4.3 | Generate final reconciliation reports | 1 hr | [ ] |
| 4.4 | Functional sign-off by all leads | 1 hr | [ ] |
| 4.5 | Wave 4 completion documentation | 30 min | [ ] |

**Total Estimated Duration:** 2-3 days

---

## Validation & Sign-Off Checklist

### CO Planning Data Validation

#### Data Load Validation
- [ ] Total planning record count reconciles (S/4HANA = ECC)
- [ ] Planning data loaded for current fiscal year
- [ ] All cost centers have planning data (or documented exceptions)
- [ ] All cost elements have planning data (or documented exceptions)
- [ ] Planning amounts are reasonable
- [ ] Currency codes are correct per company code
- [ ] No duplicate planning records

#### System Validation
- [ ] Cost center planning reports work (KP06)
- [ ] Plan/actual comparison reports work
- [ ] Planning data accessible in standard reports
- [ ] Budget control works correctly (if activated)
- [ ] Planning change functionality works (KP06)

#### Functional Validation
- [ ] Business users can view planning data
- [ ] Planning reports match expected format
- [ ] Variance calculations are correct
- [ ] Period planning totals match annual planning

**Sign-Off:**
- [ ] CO Lead: _________________ Date: _______
- [ ] Business Planning Manager: _________________ Date: _______

### Project Master & Budgets Validation

#### Data Load Validation
- [ ] Total project count reconciles (S/4HANA = ECC)
- [ ] Total WBS element count by level reconciles
- [ ] WBS hierarchy structure is complete
- [ ] All projects have budgets
- [ ] Budget amounts are reasonable
- [ ] Project dates are logical (start before end)
- [ ] Profit center assignments are correct
- [ ] Cost center assignments are correct (if used)

#### System Validation
- [ ] Projects display correctly in Project Builder (CJ20N)
- [ ] WBS hierarchy navigation works
- [ ] Project budgets display correctly (CJ33)
- [ ] Project reports are accessible
- [ ] Postings to WBS elements work

#### Functional Validation
- [ ] Project managers can access their projects
- [ ] Budget availability check works (if activated)
- [ ] Project reporting is functional
- [ ] Project change functionality works
- [ ] Settlement configuration is ready (separate task)

**Sign-Off:**
- [ ] PS Lead: _________________ Date: _______
- [ ] R&D Project Manager: _________________ Date: _______
- [ ] Finance Manager: _________________ Date: _______

### COPA Characteristics Validation

#### Configuration Validation
- [ ] Operating concern is activated
- [ ] All characteristics are defined
- [ ] All value fields are defined
- [ ] Derivation rules are configured
- [ ] Data flow from SD/FI is configured
- [ ] Assessment/distribution configured (if used)

#### System Validation
- [ ] COPA line items are created from billing documents
- [ ] Characteristic values populate correctly
- [ ] Value fields calculate correctly
- [ ] Derivation rules work
- [ ] COPA reports are accessible (KE30)

#### Functional Validation
- [ ] Profitability reports work
- [ ] Characteristic drill-down works
- [ ] Report layouts are correct
- [ ] COPA planning works (if used)
- [ ] Integration with SD and FI is functional

**Sign-Off:**
- [ ] CO Lead: _________________ Date: _______
- [ ] Business Controller: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______

### Integration Testing Validation

- [ ] Planning data integrates with actual postings
- [ ] Projects accept actual cost postings
- [ ] COPA receives data from billing documents
- [ ] Budget control works across CO and PS
- [ ] Reporting data is consistent across modules
- [ ] Fiori apps display planning and project data

**Sign-Off:**
- [ ] Integration Lead: _________________ Date: _______

### Final Wave 4 Sign-Off

- [ ] All 3 Wave 4 objects loaded/configured successfully
- [ ] All validation checklists complete
- [ ] All reconciliation reports reviewed
- [ ] All functional testing passed
- [ ] No critical errors remaining
- [ ] All error logs reviewed and resolved
- [ ] All functional leads have signed off
- [ ] Wave 4 completion documentation complete
- [ ] System ready for reporting (if post Go-Live)

**Overall Wave 4 Sign-Off:**
- [ ] Data Migration Lead: _________________ Date: _______
- [ ] CO Lead: _________________ Date: _______
- [ ] PS Lead: _________________ Date: _______
- [ ] FI Lead: _________________ Date: _______
- [ ] Project Manager: _________________ Date: _______

**Wave 4 Status:** [ ] Complete [ ] Incomplete

**System Ready for Operational Use:** [ ] Yes [ ] No

**If No, Outstanding Items:**
1. 
2. 
3. 

---

## Troubleshooting Reference

### Common Issues & Resolutions

#### CO Planning Data Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Planning load fails - "Cost center not found" | Cost center doesn't exist or inactive | Verify cost center loaded in Wave 1; Check cost center validity dates | CO Lead |
| Planning load fails - "Cost element not found" | Cost element doesn't exist or inactive | Verify cost element loaded in Wave 1; Check cost element in controlling area | CO Lead |
| Planning load fails - "Version not found" | Planning version not configured | Create planning version via OKEQ; Check version in controlling area | CO Lead |
| Duplicate planning record error | Multiple planning entries for same key | Check for duplicate cost center, cost element, period, version combination | Migration Lead |
| Planning report shows zero values | Planning not loaded or filtered out | Verify planning data via SE16 on table COSP; Check report selection criteria | CO Lead |
| Budget control not working | Budget control not activated or planning missing | Activate budget control via SPRO; Verify planning data exists | CO Lead |

#### Project Master Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Project load fails - "Profit center not found" | Profit center doesn't exist | Verify profit center loaded in Wave 1; Update project master data | CO/PS Lead |
| Project load fails - "WBS element already exists" | Duplicate WBS element in file or system | Check for duplicates; Use different WBS element ID | PS Lead |
| WBS hierarchy error | Parent WBS not loaded or circular reference | Load parent WBS first; Check hierarchy structure for loops | PS Lead |
| Budget upload fails | WBS element not found or budget format error | Verify WBS element exists; Check budget amount format (numeric) | PS Lead |
| Project status incorrect | Status not configured or invalid status code | Configure project status in IMG; Use valid status code | PS Lead |
| Settlement rule error | Settlement profile not configured | Configure settlement profile in SPRO (separate from migration) | PS Lead |

#### COPA Configuration Issues

| Issue | Possible Cause | Resolution | Escalate To |
|-------|---------------|------------|-------------|
| Operating concern not activated | Configuration incomplete or not generated | Complete configuration; Generate operating concern via KEA0 | CO Lead |
| Characteristic not found | Characteristic not added to operating concern | Add characteristic via KEA5; Regenerate operating concern | CO Lead |
| Value field error | Value field not defined or incorrect data type | Define value field via KEA6; Check data type (amount/quantity) | CO Lead |
| Derivation not working | Derivation rule not configured or master data missing | Configure derivation via KEDR; Verify master data exists | CO Lead |
| COPA line item not created | Data flow not configured or billing not transferred | Configure actual data flow via KEAT; Run transfer program KE4R | CO Lead |
| COPA report empty | No COPA data or report selection incorrect | Verify COPA line items exist (KE24); Check report selection | CO Lead |

### Escalation Path

| Level | Contact | Response Time | Issues Handled |
|-------|---------|---------------|----------------|
| **Level 1: Technical Team** | Migration Team Members | Immediate | Data errors, file format issues, standard migration errors |
| **Level 2: Functional Leads** | CO/PS Leads | 1-2 hours | Configuration issues, business logic validation, functional testing failures |
| **Level 3: Project Manager** | Project Manager | 2-4 hours | Resource issues, timeline delays, cross-functional dependencies |
| **Level 4: Executive Sponsor** | Executive Sponsor | 4-8 hours | Critical blockers, go/no-go decisions, major scope changes |

### Key Contacts

| Role | Name | Email | Phone | Availability |
|------|------|-------|-------|--------------|
| Data Migration Lead | TBD | TBD | TBD | Business hours |
| FI/CO Lead | Frey Zheng | TBD | TBD | Business hours + on-call |
| PS Lead | TBD | TBD | TBD | Business hours + on-call |
| Project Manager | TBD | TBD | TBD | Business hours + on-call |
| Business Planning Manager | TBD | TBD | TBD | Business hours |
| SAP Basis Support | TBD | TBD | TBD | 24/7 |

### Useful Transaction Codes

#### CO Planning
- `KP04` - Cost Center Planning Layout
- `KP06` - Cost Center Planning Display/Change
- `KP26` - Cost Center: Change Plan
- `OKEQ` - Maintain Versions
- `S_ALR_87013611` - Cost Center: Actual/Plan/Variance
- `KSB1` - Cost Center Line Items

#### Project System
- `CJ20N` - Project Builder
- `CJ01` - Create Project
- `CJ02` - Change Project
- `CJ03` - Display Project
- `CJ30` - Create Budget
- `CJ32` - Change Budget
- `CJ33` - Display Budget
- `CJ37` - Budget Upload
- `CN41` - WBS Element Display
- `CN43` - Project List
- `S_ALR_87013558` - Project Cost/Budget Report

#### COPA (Profitability Analysis)
- `KEA0` - Maintain Operating Concern
- `KEA5` - Maintain Characteristics
- `KEA6` - Maintain Value Fields
- `KEDR` - Maintain Derivation Rules
- `KEAT` - Actual Data Flow
- `KE24` - COPA Line Items
- `KE30` - Run Profitability Report
- `KE4R` - Transfer Billing Documents
- `KE5Z` - COPA Planning
- `KEU1` - Create Assessment Cycle
- `KEU5` - Create Distribution Cycle

#### Migration Tools
- `LTMC` - Migration Cockpit
- `LTMOM` - Migration Object Modeler
- `SLG1` - Application Log

#### System & Reporting
- `SE16` - Data Browser
- `SM37` - Job Overview
- `FB50` - Post GL Document (to cost center or WBS)

---

## Document Control

**Version History:**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 2025 | Data Migration Team | Initial version |

**Approval:**

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Data Migration Lead | TBD | | |
| FI/CO Lead | Frey Zheng | | |
| PS Lead | TBD | | |
| Business Planning Manager | TBD | | |
| Project Manager | TBD | | |

---

**End of Wave 4 Execution Runbook**

**Related Documents:**
- Migration Plan Detailed (migration-plan-detailed.md)
- Wave 4 Dependencies Flow Diagram (wave4-dependencies-flow.mmd)
- Wave 1 Execution Runbook (wave1-execution-runbook.md)
- Wave 2 Execution Runbook (wave2-execution-runbook.md)
- Wave 3 Execution Runbook (wave3-execution-runbook.md - if exists)

---

