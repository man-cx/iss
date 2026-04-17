enc# Home Control SAP S/4HANA Implementation - Filing Framework

> **Project Context:** For project overview, team structure, timeline, and objectives, see [`00_Project_Charter.md`](00_Project_Charter.md).

> **⚠️ Document Authority:** In case of any discrepancies among project files, [`00_Project_Charter.md`](00_Project_Charter.md) shall be considered the **final and authoritative source**. All other documents should be reconciled against the Project Charter.

---

## Filing Framework Guide

**Purpose:** Standardized folder structure for "Hybrid" filing (Legal/Human compliance + AI/Vector readiness).  
**Strategy:** "Phase-Based" folders with "Side-by-Side" file formats (PDF + Markdown/CSV).

### Phase Structure

**01_Prepare (Initiation)**  
Focus: Contractual Scope & Team Setup

**02_Explore (Design)**  
Focus: Business Requirements & Key Decisions

**03_Realize (Build)**  
Focus: Technical Specifications & Configuration

**04_Deploy (Validation)**  
Focus: Testing, Cutover, and Go-Live Approval

**05_Run (Support & Handover)**  
Focus: Stability Proof & User Enablement

**06_Commercials (Internal Access Only)**  
Focus: Financial Reconciliation

> **Note:** For detailed file requirements and current status of each phase, see the `README.md` file within each phase folder.

---

## File Hygiene Rules

1.  **Naming Convention:** `[Phase]_[Type]_[Description]_[Date/Ver]`.
    *   *Bad:* `New Microsoft Word Document.docx`
    *   *Good:* `03_Spec_P006_OpenPO_v2.docx`
2.  **The "CSV Rule":** If you save a critical Excel tracker (Issue Log, KDD), immediately `Save As` a CSV copy in the same folder.
3.  **The "Context Rule":** If saving a raw email (`.msg`), rename it to summarize the decision (e.g., `Email_Rocky_Agrees_to_PPCA_Scope.msg`).

---

**Reference Documents:**
- [`00_Project_Charter.md`](00_Project_Charter.md) - Project context, team structure, timeline, and objectives (anchor document for filing and analysis; **final authority for resolving discrepancies**)
- Phase `README.md` files - Detailed file requirements and current status for each phase
