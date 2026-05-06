# SAP ECC to S/4HANA Data Migration Plan - Home Control

**Document Version:** 1.0  
**Date:** November 2025  
**Project:** Home Control SAP S/4HANA Cloud Implementation  
**Migration Approach:** Big Bang with Multi-Wave Execution

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Migration Approach](#migration-approach)
3. [Wave 1: Foundation Master Data](#wave-1-foundation-master-data)
4. [Wave 2: Business Partner & Material Master](#wave-2-business-partner--material-master)
5. [Wave 3: Transactional Data & Open Items](#wave-3-transactional-data--open-items)
6. [Wave 4: Cost & Planning Data](#wave-4-cost--planning-data)
7. [Critical Path & Dependencies](#critical-path--dependencies)
8. [Migration Tools & Methods](#migration-tools--methods)
9. [Risk Mitigation](#risk-mitigation)
10. [Success Criteria](#success-criteria)

---

## Executive Summary

This document outlines the comprehensive data migration plan for Home Control's transition from SAP ECC to S/4HANA Cloud Public Edition. The migration covers **39 data objects** organized into **4 waves** based on technical dependencies and business priorities.

### Key Statistics
- **Source System:** SAP ECC
- **Target System:** SAP S/4HANA Cloud Public Edition
- **Total Data Objects:** 39
- **Migration Waves:** 4
- **Company Codes:** 7 (SG21, CN13, CN17, US10, BE10, HCIL, BR10)
- **Timeline:** 4 weeks before Go-Live to Post Go-Live

### Migration Philosophy
- **Master Data First:** All master data must be complete and validated before transactional data
- **Dependency-Driven:** Strict adherence to SAP data dependencies
- **Quality Over Speed:** Multiple validation checkpoints and reconciliation
- **Parallel Processing:** Objects within same wave can be migrated in parallel where no dependencies exist

---

## Migration Approach

### Overall Strategy
- **Migration Method:** Standard SAP migration tools and templates
- **Cutover Strategy:** Big Bang approach with parallel run capability
- **Data Freeze Period:** 48 hours before final cutover
- **Mock Cutover:** Full dress rehearsal 2 weeks before Go-Live
- **Rollback Plan:** Documented for each wave

### Module Coverage
- **FI (Financial Accounting):** GL, AP, AR, Bank Accounting
- **CO (Controlling):** Cost Centers, Profit Centers, Internal Orders, Projects
- **MM (Materials Management):** Procurement, Inventory, Info Records
- **PP (Production Planning):** BOMs, Routings (if applicable)
- **SD (Sales & Distribution):** Customer Master, Pricing, Sales Documents

---

## Wave 1: Foundation Master Data

**Timing:** T-4 weeks before Go-Live  
**Objective:** Establish organizational structure and foundational master data  
**Duration:** 3-5 days  
**Prerequisites:** None (first wave)

### Data Objects - Wave 1

| # | Data Object | Source | Dependencies | Complexity | Volume | Migration Tool | Priority |
|---|-------------|--------|--------------|------------|--------|----------------|----------|
| **1.1 Organizational Structure** |
| 1 | Chart of Accounts | ECC | None | Low | 1 CoA (YCOA) | Manual Config | Critical |
| 2 | Company Code Structure | ECC | CoA | Low | 7 entities | Migration Cockpit | Critical |
| **1.2 FI Foundation** |
| 3 | GL Account Master | ECC | CoA | Medium | ~1,000 accounts | FI_GL_ACCOUNT template | Critical |
| 4 | Bank Master Data | ECC | None | Low | ~50 banks | FI_BANK template | High |
| 5 | Tax Codes | ECC | GL Accounts | Low | ~40 codes | Manual Config | High |
| 6 | Payment Terms | ECC | None | Low | TBD | Manual Config | High |
| **1.3 CO Foundation** |
| 7 | Cost Center Master | ECC | GL Accounts | Low | TBD | CO_COST_CENTER template | Critical |
| 8 | Cost Center Hierarchy | ECC | Cost Centers | Low | HC01 | Manual/Upload | High |
| 9 | Profit Center Master | ECC | None | Low | TBD | CO_PROFIT_CENTER template | Critical |
| 10 | Profit Center Hierarchy | ECC | Profit Centers | Low | HC01 | Manual/Upload | High |
| 11 | Primary Cost Elements | ECC | GL Accounts | Low | Auto-created | System Automatic | High |
| 12 | Secondary Cost Elements | ECC | Primary Cost Elements | Low | TBD | Manual Creation | Medium |
| 13 | Statistical Key Figures | ECC | None | Low | TBD | Manual Creation | Medium |
| **1.4 Asset Accounting** |
| 14 | Fixed Asset Master | ECC | GL Accounts, Cost Centers | High | TBD | FI_ASSET_MASTER template | Critical |

### Wave 1 - Critical Success Factors
- ✅ All GL accounts must have correct reconciliation account assignments
- ✅ Cost centers must be assigned to valid profit centers
- ✅ Asset master must have correct depreciation area configurations
- ✅ All organizational validations must pass before proceeding to Wave 2

### Wave 1 - Validation Checkpoints
1. All company codes configured with correct currencies and fiscal year variant
2. GL account balances reconcile to zero (only master data, no balances yet)
3. Cost center/profit center assignments are complete
4. Fixed asset classes configured with correct GL account determination

---

## Wave 2: Business Partner & Material Master

**Timing:** T-3 weeks before Go-Live  
**Objective:** Load operational master data for procurement and sales  
**Duration:** 5-7 days  
**Prerequisites:** Wave 1 complete and validated

### Data Objects - Wave 2

| # | Data Object | Source | Dependencies | Complexity | Volume | Migration Tool | Priority |
|---|-------------|--------|--------------|------------|--------|----------------|----------|
| **2.1 Business Partners** |
| 15 | BP - Vendors (Supplier) | ECC | GL Accounts, Payment Terms, Bank Master | High | <1,200 | BP_VENDOR template | Critical |
| 16 | BP - Customers | ECC | GL Accounts, Payment Terms | Medium | TBD | BP_CUSTOMER template | Critical |
| **2.2 Material Master** |
| 17 | Material Master | Spreadsheet/ECC | GL Accounts, Material Groups | Medium | Hundreds | MM_MATERIAL_MASTER / API | Critical |
| **2.3 Procurement Master Data** |
| 18 | Purchasing Info Records | Manual/ECC | Vendors, Materials | Medium | None in legacy | MM_INFO_RECORD template | High |
| 19 | Source Lists | Manual/ECC | Info Records | Low | None in legacy | MM_SOURCE_LIST template | High |
| 20 | Quota Arrangements | ECC | Source Lists | Low | TBD | Manual/API | Medium |
| **2.4 Production Master Data** |
| 21 | Bill of Materials (BOM) | Manual | Material Master | Medium | TBD | BOM API / Upload Program | Critical |
| **2.5 Sales Master Data** |
| 22 | Customer Pricing Conditions | ECC | Customers, Materials | Low | TBD | SD_PRICING template | High |
| 23 | Credit Accounts | ECC | Customers | Low | TBD | Manual Configuration | Medium |
| 24 | Customer Material Info | ECC | Customers, Materials | Low | TBD | SD_CUST_MATERIAL template | Medium |

### Wave 2 - Critical Success Factors
- ✅ Vendor/Customer reconciliation accounts correctly assigned
- ✅ Material master has complete procurement and MRP views
- ✅ Info records have valid price and lead time data
- ✅ BOMs are complete and multi-level structures validated
- ✅ No duplicate business partner records

### Wave 2 - Validation Checkpoints
1. Business Partner master data completeness: 100% for active vendors/customers
2. Material master coverage: All active materials with complete views (MRP, Procurement, Sales, Accounting)
3. Info record coverage: All regular procurement materials have at least one valid info record
4. BOM validation: All finished goods have valid BOMs with correct components
5. Pricing conditions loaded and tested with sample sales orders

### Wave 2 - Special Considerations
- **Material Master:** Integration with Smart-Fulfillment System for material number assignment
- **Vendor Master:** Separate number ranges for BOM/NPR vendors (Z001), IC vendors (Z002), Employees (ZEMP), One-time (ZCPD)
- **Info Records:** Use BTP App for PPCA approval workflow
- **BOMs:** Special UOM "ZPC" with 3 decimal places required

---

## Wave 3: Transactional Data & Open Items

**Timing:** T-1 week (Mock Cutover) and Go-Live Weekend  
**Objective:** Migrate open documents and balances  
**Duration:** Mock (2 days) + Final (8-12 hours)  
**Prerequisites:** Wave 1 & 2 complete and validated

### Data Objects - Wave 3

| # | Data Object | Source | Dependencies | Complexity | Volume | Migration Tool | Priority |
|---|-------------|--------|--------------|------------|--------|----------------|----------|
| **3.1 Financial Balances & Open Items** |
| 25 | GL Account Balances | ECC | GL Accounts, Cost Centers, Profit Centers | Medium | TBD | ACDOCA/FI_BALANCE template | Critical |
| 26 | GL Open Line Items | ECC | GL Accounts | Medium | TBD | FI_GL_OPEN_ITEMS template | High |
| 27 | AP Open Items | ECC | Vendors, GL Accounts | Low | TBD | FI_AP_OPEN_ITEMS template | Critical |
| 28 | AR Open Items | ECC | Customers, GL Accounts | Low | TBD | FI_AR_OPEN_ITEMS template | Critical |
| 29 | Fixed Asset Balances | ECC | Fixed Asset Master | High | TBD | FI_ASSET_TRANSACTIONS | Critical |
| **3.2 Inventory & Stock** |
| 30 | Inventory Stock Balances | ECC | Materials, Plants, Storage Locations | High | TBD | MM_STOCK template | Critical |
| 31 | Stock at Subcontractor | ECC | Materials, Vendors | Medium | TBD | MM_SUBCON_STOCK template | High |
| 32 | Physical Inventory Counts | ECC | Materials | Low | TBD | MM_PHYSICAL_INVENTORY | Low |
| **3.3 Open Procurement Documents** |
| 33 | Open Purchase Orders | ECC | Vendors, Materials, Info Records | Medium | TBD | MM_PURCHASE_ORDER template | High |
| 34 | Open Purchase Requisitions | ECC | Materials | Low | TBD | MM_PURCHASE_REQ template | Medium |
| **3.4 Open Sales Documents** |
| 35 | Open Sales Orders | ECC | Customers, Materials, Pricing | Low | TBD | SD_SALES_ORDER template | High |
| 36 | Sales Contracts | ECC | Customers, Materials | Low | TBD | SD_CONTRACT template | Medium |

### Wave 3 - Critical Success Factors
- ✅ Zero balance discrepancies between ECC and S/4HANA
- ✅ All open items migrated with correct aging and due dates
- ✅ Inventory values reconcile to penny level
- ✅ No negative stock situations created
- ✅ Open PO/SO quantities match and can be fulfilled

### Wave 3 - Validation Checkpoints
1. **FI Reconciliation:**
   - GL balance sheet totals match ECC
   - Trial balance by cost center/profit center reconciles
   - AP aging report matches ECC
   - AR aging report matches ECC
   - Fixed asset net book value equals ECC

2. **Inventory Reconciliation:**
   - Stock quantity by material/plant/storage location matches
   - Stock value reconciles by material type
   - Subcontractor stock quantities verified
   - No blocked stock migrated as unrestricted

3. **Open Documents:**
   - Open PO value and quantity reconciles
   - Open SO value and quantity reconciles
   - Contracts with remaining value correctly loaded

### Wave 3 - Data Cutoff Rules
- **Financial Data:** Cutoff as of last day of month preceding Go-Live
- **Inventory:** Physical inventory count freeze 48 hours before cutover
- **Open Documents:** No new PO/SO creation during freeze period
- **AP/AR:** All invoices posted through final cutoff date

---

## Wave 4: Cost & Planning Data

**Timing:** Post Go-Live or T-2 weeks (if needed)  
**Objective:** Load planning and project data  
**Duration:** 2-3 days  
**Prerequisites:** Wave 3 complete and system stable

### Data Objects - Wave 4

| # | Data Object | Source | Dependencies | Complexity | Volume | Migration Tool | Priority |
|---|-------------|--------|--------------|------------|--------|----------------|----------|
| **4.1 Planning Data** |
| 37 | CO Planning Data | ECC | Cost Centers, Profit Centers | Low | TBD | CO_PLAN template | Low |
| 38 | Project Master & Budgets | ECC | WBS Elements, Cost Elements | Medium | TBD | PS_PROJECT template | Medium |
| 39 | COPA Characteristics | ECC | Customers, Materials, Org | Low | TBD | COPA_CHAR template | Low |

### Wave 4 - Notes
- **Optional Wave:** May be executed post Go-Live if planning data not critical for Day 1
- **Current Year Only:** Migrate current fiscal year planning data only
- **Projects:** Focus on active R&D and tooling projects with remaining budget
- **COPA:** Load characteristics and value fields setup

---

## Critical Path & Dependencies

### Dependency Map Summary

```
Foundation Layer (Wave 1):
├─ Chart of Accounts → GL Accounts → All Financial Objects
├─ GL Accounts → Cost Centers → Asset Master
├─ GL Accounts → Profit Centers → Business Partners
└─ Cost Centers → Cost Center Hierarchy

Business Partner & Material Layer (Wave 2):
├─ GL Accounts + Profit Centers → Vendors → Info Records
├─ GL Accounts + Profit Centers → Customers → Pricing
├─ GL Accounts + Profit Centers → Materials → BOMs
└─ Info Records → Source Lists → Quota Arrangements

Transactional Layer (Wave 3):
├─ GL Accounts → GL Balances
├─ Vendors → AP Open Items
├─ Customers → AR Open Items
├─ Asset Master → Asset Balances
├─ Materials → Inventory Balances
├─ Vendors + Materials + Info Records → Open POs
└─ Customers + Materials + Pricing → Open SOs

Planning Layer (Wave 4):
├─ Cost Centers → CO Planning
├─ Cost Elements → Project Master
└─ All Master Data → COPA
```

### Critical Path Objects
These objects are on the critical path and any delay will impact downstream migration:

1. **Chart of Accounts** - Foundation for all FI/CO
2. **GL Accounts** - Required by almost all other objects
3. **Material Master** - Required by inventory, procurement, sales
4. **Vendors** - Required by AP, procurement documents
5. **Customers** - Required by AR, sales documents
6. **Inventory Balances** - High volume, requires extended processing time

### Parallel Processing Opportunities

**Within Wave 1:**
- Bank Master and Tax Codes can be loaded in parallel with GL Accounts
- Cost Center and Profit Center can be loaded in parallel

**Within Wave 2:**
- Vendor and Customer master can be loaded in parallel
- Material Master loading can overlap with Business Partner loading (after profit centers complete)
- BOM loading can begin after Material Master complete

**Within Wave 3:**
- AP Open Items and AR Open Items can be loaded in parallel
- Inventory balances can be loaded in parallel with open documents
- Open POs and Open SOs can be loaded in parallel

---

## Migration Tools & Methods

### Standard SAP Tools

| Tool | Purpose | Data Objects |
|------|---------|--------------|
| **Migration Cockpit** | Master data migration | All master data objects |
| **Standard Templates** | Pre-built migration objects | FI, CO, MM, SD templates |
| **LSMW (Legacy System Migration Workbench)** | Custom transactional data | Complex scenarios |
| **Excel Upload** | Small volume master data | BOMs, hierarchies, small master files |
| **API/OData Services** | Real-time integration | Material master with Smart-Fulfillment |
| **Direct Input Programs** | High-volume transactional | Inventory balances, FI documents |

### Migration Cockpit - Key Templates

**FI Templates:**
- FI_GL_ACCOUNT - GL Account Master
- FI_BANK - Bank Master
- FI_AP_OPEN_ITEMS - AP Open Items
- FI_AR_OPEN_ITEMS - AR Open Items
- FI_ASSET_MASTER - Fixed Asset Master
- FI_ASSET_TRANSACTIONS - Asset Transactions

**CO Templates:**
- CO_COST_CENTER - Cost Center Master
- CO_PROFIT_CENTER - Profit Center Master
- CO_COST_ELEMENT - Cost Element Master

**MM Templates:**
- MM_MATERIAL_MASTER - Material Master
- MM_INFO_RECORD - Purchasing Info Record
- MM_SOURCE_LIST - Source List
- MM_STOCK - Inventory Balances
- MM_PURCHASE_ORDER - Purchase Order

**SD Templates:**
- SD_CUSTOMER - Customer Master (Sales View)
- SD_PRICING - Pricing Conditions
- SD_SALES_ORDER - Sales Order

### Data Quality Checkpoints

**Pre-Migration (ECC):**
1. Data cleansing in source system
2. Duplicate record identification and merge
3. Inactive master data archival
4. Data completeness validation
5. Referential integrity checks

**During Migration:**
1. Field mapping validation
2. Transformation rule verification
3. Error log review and correction
4. Batch processing monitoring
5. Performance tracking

**Post-Migration (S/4HANA):**
1. Record count reconciliation
2. Balance verification
3. Aging report comparison
4. Master data completeness check
5. Integration testing

### Reconciliation Reports

| Report | Purpose | Frequency |
|--------|---------|-----------|
| FI Trial Balance | GL balance reconciliation | After each wave |
| AP Aging | Vendor open items validation | Daily during Wave 3 |
| AR Aging | Customer open items validation | Daily during Wave 3 |
| Stock Value Report | Inventory balance check | Daily during Wave 3 |
| Asset Register | Fixed asset reconciliation | After asset migration |
| Open PO Report | Purchase order validation | After PO migration |
| Open SO Report | Sales order validation | After SO migration |

---

## Risk Mitigation

### Risk Assessment & Mitigation Strategies

| Risk | Impact | Probability | Mitigation Strategy |
|------|--------|-------------|---------------------|
| **Balance Discrepancies** | High | Medium | Multiple reconciliation checkpoints, parallel run for 1 month |
| **Data Quality Issues** | High | High | Pre-migration data cleansing, validation rules, data quality dashboard |
| **Missing Dependencies** | High | Medium | Dependency matrix, pre-migration validation, staged approach |
| **Volume/Performance** | Medium | Medium | Batch processing, parallel loading, performance testing in sandbox |
| **Timing Delays** | High | Medium | Buffer time in plan, critical path management, escalation process |
| **Incomplete Master Data** | High | Medium | Master data completeness reports, mandatory field validation |
| **Integration Failures** | Medium | Low | Integration testing, Smart-Fulfillment System sync validation |
| **User Error in Validation** | Medium | Medium | Clear validation procedures, training, dual verification |

### Contingency Plans

**Scenario 1: Wave 1 Delays**
- **Trigger:** Foundation master data not complete by T-4 weeks
- **Action:** Extend Wave 1 by 3 days, compress Wave 2 by parallel loading where possible
- **Escalation:** Project Manager notified if delay exceeds 2 days

**Scenario 2: Balance Discrepancies**
- **Trigger:** Reconciliation differences > 0.1% or $10,000
- **Action:** Root cause analysis, re-extraction from ECC, re-load specific objects
- **Escalation:** Finance approval required before proceeding to next wave

**Scenario 3: High Error Rates**
- **Trigger:** Error rate > 5% in any migration object
- **Action:** Stop migration, fix source data or mapping, re-migrate
- **Escalation:** Functional lead and project manager involved

**Scenario 4: Go-Live Date Risk**
- **Trigger:** Wave 3 not complete 24 hours before Go-Live
- **Action:** Activate rollback plan, defer Go-Live by 1 week
- **Escalation:** Executive sponsor decision required

### Mock Cutover Plan

**Timing:** T-2 weeks (Weekend)

**Objectives:**
1. Test end-to-end migration process
2. Validate timing estimates
3. Identify any data quality issues
4. Train migration team
5. Test rollback procedures

**Scope:**
- Complete execution of Waves 1-3
- Full reconciliation and validation
- Issue log and remediation
- Timing and resource validation

**Success Criteria:**
- All waves complete within allocated time
- Balance reconciliation within tolerance (0.1%)
- Error rate < 2%
- Team confidence in process

---

## Success Criteria

### Overall Success Criteria

| # | Criteria | Target | Measurement Method |
|---|----------|--------|-------------------|
| 1 | **Balance Accuracy** | 100% (within $100 variance) | FI Trial Balance, Asset Register |
| 2 | **Master Data Completeness** | 100% for active records | Completeness reports by object |
| 3 | **No Duplicate Records** | 0 duplicates | Duplicate check reports |
| 4 | **Open Item Accuracy** | 100% | AP/AR Aging reports |
| 5 | **Inventory Accuracy** | 99.9% | Stock value reconciliation |
| 6 | **Data Quality** | Error rate < 1% | Migration log analysis |
| 7 | **Timeline Adherence** | +/- 1 day per wave | Project schedule tracking |
| 8 | **Integration Success** | 100% | Smart-Fulfillment sync validation |

### Wave-Specific Success Criteria

**Wave 1 Success:**
- ✅ All 14 foundation objects migrated
- ✅ GL accounts ready for posting
- ✅ CO assignments complete
- ✅ Asset master configured

**Wave 2 Success:**
- ✅ All 10 business partner and material objects migrated
- ✅ No missing vendor/customer master for active transactions
- ✅ Material master 100% complete for active materials
- ✅ BOMs validated for all manufactured items
- ✅ Info records cover 95%+ of regular procurement

**Wave 3 Success:**
- ✅ All 12 transactional objects migrated
- ✅ Zero balance discrepancies
- ✅ All open items with correct aging
- ✅ Inventory quantities and values reconcile
- ✅ Open documents can be processed in S/4HANA

**Wave 4 Success:**
- ✅ Planning data available for reporting
- ✅ Projects accessible with budget information
- ✅ COPA operational for profitability analysis

### Go-Live Readiness Criteria

**Must Have (Go/No-Go):**
1. ✅ All Wave 1-3 objects migrated and validated
2. ✅ Balance sheet balances
3. ✅ No critical errors in migration logs
4. ✅ AP/AR aging matches ECC
5. ✅ Inventory value reconciles
6. ✅ Key users trained and confident
7. ✅ Rollback plan tested and ready

**Should Have:**
1. ✅ Wave 4 objects migrated or scheduled
2. ✅ All reconciliation reports signed off
3. ✅ Integration with Smart-Fulfillment System validated
4. ✅ Migration documentation complete

**Nice to Have:**
1. Historical data archived and accessible
2. Data quality dashboard operational
3. Self-service reports available

---

## Appendices

### Appendix A: Company Code Details

| Company Code | Company Name | Currency | Fiscal Year | Ledger |
|--------------|--------------|----------|-------------|--------|
| SG21 | Home Control Singapore Pte Ltd | SGD | K4 | 0L (IFRS), 2L (SGAP) |
| CN13 | HC (Suzhou) Limited | CNY | K4 | 0L (IFRS), 2L (CNAP) |
| CN17 | Home Control Solutions (Suzhou) Limited | CNY | K4 | 0L (IFRS), 2L (CNAP) |
| US10 | Premium Home Control Solutions LLC | USD | K4 | 0L (IFRS), 2L (USAP) |
| BE10 | Home Control Europe NV | EUR | K4 | 0L (IFRS), 2L (BEAP) |
| HCIL | Home Control International Limited | KYD | K4 | 0L (IFRS), 2L (IFRS) |
| BR10 | Omni Remotes Do Brasil Ltda | BRL | K4 | 0L (IFRS), 2L (BRAP) |

### Appendix B: Material Types

Material types include: ZFER (Finished Goods), ZH01-ZH44 (various component types), ZHL1-ZHL2 (semifinished goods). Details available in MM Master Data design document.

### Appendix C: Business Partner Number Ranges

- **Z001** BOM/NPR Vendor: 0000100000-0009999999 (internal)
- **Z002** Inter Company Vendor: AAAA-ZZZZ (external)
- **ZCPD** One-time Vendor: 0000000001-0000000999 (external)
- **ZEMP** Employee: 0000010000-0000099999 (internal)

### Appendix D: Contact Information

| Role | Name | Responsibility |
|------|------|----------------|
| Project Manager | TBD | Overall migration governance |
| FI Lead | Frey Zheng | FI/CO data migration |
| MM Lead | Meos Xu | MM data migration |
| SD Lead | Warner Yu | SD data migration |
| PP Lead | Joe Wu | PP data migration |
| Data Migration Lead | TBD | Technical execution |

---

**Document Control:**
- **Version:** 1.0
- **Status:** Draft for Review
- **Next Review:** TBD
- **Approval Required:** Project Steering Committee

---

**Related Documents:**
- Migration Flow Diagram (migration-flow-diagram.mmd)
- Migration Scope Summary (dm-scope.md)
- SAP Design Documents (../../02_Explore/Design_Documents/)

