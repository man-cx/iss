# Data Objects ERD - Overview
**SAP ECC to S/4HANA Data Migration - Home Control**

## ERD Files by Wave

The Entity-Relationship Diagrams have been organized into separate files for each migration wave, making it easier to view and understand the data model progressively.

### 📁 File Locations

| Wave | File | Objects | Description |
|------|------|---------|-------------|
| **Wave 1** | [wave-1/wave1-data-objects-erd.mmd](wave-1/wave1-data-objects-erd.mmd) | 14 | Foundation master data (Chart of Accounts, Company Code, GL Accounts, Cost Centers, Profit Centers, Fixed Assets) |
| **Wave 2** | [wave-2/wave2-data-objects-erd.mmd](wave-2/wave2-data-objects-erd.mmd) | 10 | Business partners & material master (Vendors, Customers, Materials, Info Records, BOMs) |
| **Wave 3A** | [wave-3/wave3a-financial-balances-erd.mmd](wave-3/wave3a-financial-balances-erd.mmd) | 5 | Financial balances & open items (GL Balance, GL/AP/AR Open Items, Asset Balance) |
| **Wave 3B** | [wave-3/wave3b-inventory-documents-erd.mmd](wave-3/wave3b-inventory-documents-erd.mmd) | 7 | Inventory & open documents (Inventory Stock, Subcon Stock, Physical Inventory, Open PO/PR, Open SO/Contracts) |
| **Wave 4** | [wave-4/wave4-data-objects-erd.mmd](wave-4/wave4-data-objects-erd.mmd) | 3 | Cost & planning data (CO Planning, Projects, COPA) |

**Total:** 39 data objects across 4 waves

---

## Wave Dependencies

```
Wave 1 (Foundation)
    ↓
    Provides: Chart of Accounts, Company Codes, GL Accounts, 
              Cost Centers, Profit Centers, Payment Terms, 
              Bank Master, Tax Codes, Fixed Assets
    ↓
Wave 2 (Business Partners & Materials)
    ↓
    Depends on: GL Accounts (reconciliation), Profit Centers, 
                Payment Terms, Bank Master
    Provides: Vendors, Customers, Materials, Info Records, BOMs
    ↓
Wave 3 (Transactional Data)
    ↓
    Depends on: All Wave 1 & Wave 2 objects
    Provides: Balances, Open Items, Inventory, Open Documents
    ↓
Wave 4 (Planning)
    ↓
    Depends on: Cost Centers, Profit Centers, Cost Elements,
                Customers, Materials
    Provides: Planning data, Projects, COPA
```

---

## Key Relationships Across Waves

### 🔑 Critical Dependencies

**From Wave 1 → Wave 2:**
- `GL_ACCOUNT` → `VENDOR` (reconciliation account)
- `GL_ACCOUNT` → `CUSTOMER` (reconciliation account)
- `GL_ACCOUNT` → `MATERIAL_MASTER` (valuation account)
- `PROFIT_CENTER` → `VENDOR`, `CUSTOMER`, `MATERIAL_MASTER`
- `PAYMENT_TERMS` → `VENDOR`, `CUSTOMER`
- `BANK_MASTER` → `VENDOR`

**From Wave 1 & 2 → Wave 3A (Financial):**
- `GL_ACCOUNT` → `GL_BALANCE`, `GL_OPEN_ITEMS`, `AP_OPEN_ITEMS`, `AR_OPEN_ITEMS`
- `VENDOR` → `AP_OPEN_ITEMS`
- `CUSTOMER` → `AR_OPEN_ITEMS`
- `FIXED_ASSET` → `ASSET_BALANCE`
- `COST_CENTER`, `PROFIT_CENTER` → `GL_BALANCE`, `GL_OPEN_ITEMS`
- `PAYMENT_TERMS` → `AP_OPEN_ITEMS`, `AR_OPEN_ITEMS`

**From Wave 1 & 2 → Wave 3B (Inventory & Documents):**
- `MATERIAL_MASTER` → `INVENTORY_STOCK`, `SUBCONTRACTOR_STOCK`, `PHYSICAL_INVENTORY`, `OPEN_PURCHASE_ORDER`, `OPEN_PURCHASE_REQ`, `OPEN_SALES_ORDER`, `SALES_CONTRACT`
- `VENDOR` → `SUBCONTRACTOR_STOCK`, `OPEN_PURCHASE_ORDER`
- `CUSTOMER` → `OPEN_SALES_ORDER`, `SALES_CONTRACT`
- `INFO_RECORD` → `OPEN_PURCHASE_ORDER`
- `COMPANY_CODE` → `OPEN_PURCHASE_ORDER`

**From Wave 1 → Wave 4:**
- `COST_CENTER` → `CO_PLANNING`, `PROJECT_MASTER`
- `PROFIT_CENTER` → `PROJECT_MASTER`, `COPA_CHARACTERISTICS`
- `PRIMARY_COST_ELEMENT`, `SECONDARY_COST_ELEMENT` → `CO_PLANNING`

**From Wave 2 → Wave 4:**
- `CUSTOMER` → `COPA_CHARACTERISTICS`
- `MATERIAL_MASTER` → `COPA_CHARACTERISTICS`

---

## How to Use These Diagrams

### Note on Wave 3 Split

Wave 3 has been divided into two separate ERD diagrams for clarity:

- **Wave 3A (Financial Balances):** Focuses on financial reconciliation - GL balances, open items (GL, AP, AR), and asset balances. These objects are tightly integrated with FI/CO and require precise balance reconciliation.

- **Wave 3B (Inventory & Documents):** Focuses on operational transactions - inventory stock, open procurement documents (PO, PR), and open sales documents (SO, Contracts). These objects are centered around material movements and business operations.

This split makes it easier to:
- Understand the two distinct domains within transactional data
- Plan separate validation strategies (financial reconciliation vs. operational fulfillment)
- Execute parallel loading where appropriate

### 1. **Understanding Dependencies**
Each wave's ERD shows:
- Objects within that wave (full entity definitions)
- Referenced objects from previous waves (simplified references)
- Relationships within the wave
- Relationships to previous waves

### 2. **Load Sequence Validation**
Use the ERDs to:
- Verify parent objects exist before loading child objects
- Identify required foreign key fields
- Plan referential integrity checks

### 3. **Data Quality Checks**
For each relationship shown:
- Pre-Import: Validate foreign key values exist in source
- Post-Import: Verify referential integrity in S/4HANA

### 4. **Impact Analysis**
When an object fails to load:
- Check the ERD to see what downstream objects are affected
- Identify which relationships need to be validated

---

## Key Fields Legend

| Symbol | Meaning |
|--------|---------|
| PK | Primary Key |
| FK | Foreign Key |
| PK,FK | Primary Key that is also a Foreign Key |

---

## Relationship Notation

| Symbol | Cardinality | Meaning |
|--------|-------------|---------|
| `||--o{` | One to Many | One parent can have many children |
| `}o--||` | Many to One | Many children belong to one parent |
| `||--||` | One to One | One-to-one relationship |

---

## Viewing the Diagrams

These Mermaid ERD files can be viewed in:
- **GitHub:** Renders automatically in markdown preview
- **VS Code:** With Mermaid extension
- **Mermaid Live Editor:** https://mermaid.live
- **Confluence/Wiki:** With Mermaid plugin

---

**Document Version:** 1.0  
**Last Updated:** November 2025  
**Related Documents:**
- [Migration Plan Detailed](migration-plan-detailed.md)
- [Migration Flow Diagram](migration-flow-diagram.mmd)
- Wave-specific execution runbooks and flow diagrams

