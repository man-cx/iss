# Supplier Info Record Validation - Mermaid Diagrams

This folder contains three Mermaid diagrams that visualize the data validation flow for Supplier Info Record migration.

## Diagram Files

### 1. `supplier-info-validation-flow.mmd` - High-Level Flow Diagram
**Purpose:** Shows the overall data flow across all teams and systems

**Best for:**
- Understanding the big picture
- Seeing how different teams interact
- Identifying handoff points between teams

**Key Features:**
- 5 actors/systems: ECC Team, Validation Team, Business Team, Public Cloud Team, Public Cloud System
- 4 validation stages clearly marked
- Decision points with pass/fail paths
- Color-coded by actor type

**Use this when:** Presenting to stakeholders or explaining the overall process

---

### 2. `supplier-info-validation-swimlane.mmd` - Swimlane Diagram
**Purpose:** Shows clear separation of responsibilities across teams

**Best for:**
- Understanding who does what
- Identifying team dependencies
- Planning resource allocation
- Tracking handoffs between teams

**Key Features:**
- 5 horizontal swimlanes (one per actor)
- Chronological left-to-right flow
- Stage boundaries clearly marked
- Key decision points highlighted

**Use this when:** 
- Planning project roles and responsibilities
- Creating RACI matrices
- Explaining the process to team members

---

### 3. `supplier-info-validation-detailed.mmd` - Detailed Validation Logic
**Purpose:** Shows every validation checkpoint and decision logic

**Best for:**
- Understanding the detailed validation sequence
- Implementing the validation logic
- Troubleshooting failed validations
- Understanding all decision points and error paths

**Key Features:**
- All 9 Stage 1 validations shown individually (1.1-1.9)
- All Stage 2, 3, 4 validation groups
- Every decision point with pass/fail paths
- Critical error stops clearly marked
- Business review points highlighted
- Rework loops shown

**Use this when:**
- Implementing the validation code
- Debugging validation failures
- Training the validation team
- Creating test cases

---

## How to View the Diagrams

### Option 1: GitHub/GitLab
If these files are in a repository, GitHub and GitLab will render Mermaid diagrams automatically when you view the `.mmd` files.

### Option 2: Mermaid Live Editor
1. Go to https://mermaid.live/
2. Copy the contents of any `.mmd` file
3. Paste into the editor
4. The diagram will render automatically

### Option 3: VS Code Extension
1. Install the "Markdown Preview Mermaid Support" extension
2. Create a markdown file with the mermaid code block:
   ````markdown
   ```mermaid
   [paste mermaid code here]
   ```
   ````
3. Open preview (Ctrl+Shift+V or Cmd+Shift+V)

### Option 4: Command Line (mermaid-cli)
```bash
# Install mermaid-cli
npm install -g @mermaid-js/mermaid-cli

# Generate PNG
mmdc -i supplier-info-validation-flow.mmd -o flow-diagram.png

# Generate SVG
mmdc -i supplier-info-validation-flow.mmd -o flow-diagram.svg

# Generate PDF
mmdc -i supplier-info-validation-flow.mmd -o flow-diagram.pdf
```

---

## Diagram Legend

### Colors

**Flow Diagrams:**
- 🔵 Blue: ECC Extraction Team activities
- 🟡 Yellow: Data Validation Team activities
- 🟢 Green: Business/Purchasing Team activities
- 🟣 Purple: Public Cloud Team activities
- 🔷 Teal: Public Cloud System activities

**Stages:**
- 🔵 Light Blue: Stage 1 (Post-Extraction Validation)
- 🟠 Orange: Stage 2 (Template Validation)
- 🟣 Purple: Stage 3 (Post-Import Validation)
- 🟢 Green: Stage 4 (Reconciliation)

**Status:**
- 🟢 Green: Success/Approval/Go-Live
- 🔴 Red: Critical Error/Stop
- 🟡 Yellow: Review Required
- 🔷 Cyan: Configuration/Preparation

### Shapes

- **Rectangle**: Process/Activity
- **Diamond**: Decision Point
- **Rounded Rectangle**: Start/End Point
- **Subgraph/Box**: Actor/Team/Stage grouping

---

## Quick Reference: Validation Stages

### Stage 1: Post-Extraction Validation (9 validations)
- 1.1: Header Data Quality
- 1.2: Purchasing Org Data Quality
- 1.3: Vendor and Material Existence
- 1.4: Orphaned Purchasing Org Records
- 1.5: Duplicate Info Records
- 1.6: Invalid Purchasing Groups
- 1.7: Tax Codes Inventory
- 1.8: Price Date Issues
- 1.9: Tolerance and Quantity Settings

### Stage 2: Template Validation (8 validations)
- 2.1: Required Fields Check
- 2.2: Data Format Check
- 2.3: Duplicate Records Check
- 2.4: Referential Integrity (Vendor/Material Existence)
- 2.5: Business Logic Validation
- 2.6: Currency Code Validation
- 2.7: Unit of Measure Validation
- 2.8: Record Count Summary

### Stage 3: Post-Import Validation (8 validations)
- 3.1: Import Success Rate
- 3.2: Record Count Verification
- 3.3: Price Accuracy Spot Check
- 3.4: Vendor-Material Relationships
- 3.5: Critical Info Records Verification
- 3.6: Pricing Completeness
- 3.7: Purchasing Organization Assignment
- 3.8: Delivery Time Validation

### Stage 4: Reconciliation (5 validations)
- 4.1: Full Record Count Comparison
- 4.2: Sample Record Comparison
- 4.3: Price Comparison Report
- 4.4: Missing Records Analysis
- 4.5: Extra Records Analysis

---

## Critical Decision Points

### STOP Points (Migration Cannot Proceed)
1. **Missing Master Data** (Validation 1.3)
   - Vendors or materials don't exist in master data files
   - Action: Request complete master data from ECC team

2. **Missing Currency with Valid Price** (Validation 1.2)
   - Critical data quality issue
   - Action: Send back to ECC team for correction

3. **Data Integrity Issues** (Validation 1.4)
   - Orphaned purchasing org records
   - Action: Request re-extraction with proper joins

4. **Min > Max Quantity** (Validation 1.9)
   - Business logic violation
   - Action: Send back to ECC team for correction

5. **Import Success Rate < 85%** (Validation 3.1)
   - Systematic import failures
   - Action: Fix template issues and retry

### Business Review Required
1. **Zero Prices** (Validation 1.2)
   - May be valid for consignment/free items
   - Action: Document and get approval

2. **Duplicates** (Validation 1.5)
   - May be intentional (different categories)
   - Action: Decide which to keep

3. **Expired Prices** (Validation 1.8)
   - Prices > 2 years old
   - Action: Review and approve for migration

4. **UAT Failures** (Stage 4)
   - Users find issues in functionality
   - Action: Fix and retest

---

## Tips for Using These Diagrams

### For Project Managers
- Use **swimlane diagram** for resource planning
- Use **flow diagram** for stakeholder presentations
- Use **detailed diagram** for risk assessment (identify critical paths)

### For Developers/Implementers
- Use **detailed diagram** as implementation blueprint
- Each validation box = one function/script to implement
- Decision diamonds = if/else logic in code

### For Business Analysts
- Use **flow diagram** to understand data lineage
- Use **detailed diagram** to identify business review points
- Use for creating test scenarios

### For Testers
- Use **detailed diagram** to create test cases
- Each decision point = test scenario
- Each validation = test suite

---

## Updating the Diagrams

If the validation process changes:

1. Edit the `.mmd` file directly (Mermaid syntax)
2. Test changes in Mermaid Live Editor
3. Update this README if new stages/validations are added
4. Regenerate images if using in presentations

### Common Changes
- Adding new validations: Add new box and decision diamond
- Changing decision criteria: Update diamond labels
- Adding new actors: Add new subgraph/swimlane
- Changing flow: Redirect arrows

---

## Related Documentation

- **supplier-info-validation.md**: Detailed validation procedures (what these diagrams visualize)
- **supplier-info-extraction.md**: SQL queries for data extraction
- **supplier-info-template-mapping.md**: Field mapping rules
- **supplier-info-migration-steps.md**: Step-by-step execution checklist

---

## Questions or Issues?

If the diagrams are unclear or need updates:
1. Check the source validation document (`supplier-info-validation.md`)
2. Review the logic in the detailed diagram
3. Update diagrams to match current process
4. Document changes in this README

---

**Document Version:** 1.0  
**Last Updated:** [Date]  
**Project:** SAP ECC 6.0 to SAP ERP Public Cloud Migration  
**Author:** Migration Team

