# BOM Template Mapping Guide

## Overview
This guide provides field-by-field mapping between SAP ECC 6.0 BOM tables and SAP ERP Public Cloud standard import templates.

## SAP ERP Public Cloud Standard Template Structure

### Template: Material BOM Import

The standard template typically includes the following columns (based on SAP Public Cloud API structure):

## Field Mapping Tables

### BOM Header Mapping

| Template Column | Required | SAP ECC Source | Table.Field | Transformation Rule | Example Value |
|----------------|----------|----------------|-------------|---------------------|---------------|
| Material | Yes | Material Number | MAST.MATNR | Remove leading zeros | FG001 or 000000000FG001 → FG001 |
| Plant | Yes | Plant | MAST.WERKS | Direct mapping | 1000 |
| BOMUsage | Yes | BOM Usage | MAST.STLAN | Direct mapping (usually '1' for Production) | 1 |
| AlternativeBOM | No | Alternative BOM | MAST.STLAL | Direct mapping, default '01' if blank | 01 |
| BOMHeaderBaseUnit | Yes | Base Unit | STKO.BMEIN | Direct mapping | EA, KG, L |
| BOMHeaderQuantity | Yes | Base Quantity | STKO.BMENG | Direct mapping, default 1.000 | 1.000 |
| BOMHeaderText | No | BOM Text | STKO.ZTEXT | Direct mapping if exists | Production BOM |
| ValidityStartDate | No | Valid From | STKO.DATUV | Convert to ISO format YYYY-MM-DD | 2024-01-01 |
| EngineeringChangeDocument | No | ECM Number | STKO.AENNR | Direct mapping if used | ECN-001 |
| IsConfiguredMaterial | No | Configuration | STKO.CSLTY | Map to true/false | false |
| BOMHeaderStatus | No | BOM Status | STKO.STLST | Map status codes | 01 → Active |

### BOM Item Mapping

| Template Column | Required | SAP ECC Source | Table.Field | Transformation Rule | Example Value |
|----------------|----------|----------------|-------------|---------------------|---------------|
| Material | Yes | Parent Material | MAST.MATNR | Remove leading zeros (same as header) | FG001 |
| Plant | Yes | Plant | MAST.WERKS | Direct mapping (same as header) | 1000 |
| BOMUsage | Yes | BOM Usage | MAST.STLAN | Direct mapping (same as header) | 1 |
| AlternativeBOM | No | Alternative BOM | MAST.STLAL | Direct mapping (same as header) | 01 |
| BOMItemNumber | Yes | Item Number | STPO.POSNR | Format as 4-digit string | 0010, 0020 |
| BOMItemCategory | No | Item Category | STPO.POSTP | Map category codes | L → Stock Item |
| BOMItemComponent | Yes | Component Material | STPO.IDNRK | Remove leading zeros | RM001 |
| BOMItemQuantity | Yes | Component Quantity | STPO.MENGE | Direct mapping with decimals | 2.500 |
| BOMItemUnit | Yes | Component Unit | STPO.MEINS | Direct mapping | KG, L, EA |
| ComponentScrapPercent | No | Component Scrap | STPO.AUSCH | Direct mapping as percentage | 5 |
| OperationNumber | No | Operation Reference | STPO.AVOAU | Direct mapping if routing used | 0010 |
| ValidityStartDate | No | Valid From Date | STPO.DATUV | Convert to ISO format | 2024-01-01 |
| ValidityEndDate | No | Valid To Date | STPO.DATUB | Convert to ISO format, use 9999-12-31 if blank | 9999-12-31 |
| IsFixedQuantity | No | Fixed Quantity Flag | STPO.FMENG | Map X to true, blank to false | false |
| IsMaterialProvision | No | Provision Indicator | STPO.ALPRF | Map to true/false | true |
| BOMItemText | No | Item Text | STPO.POTX1 | Direct mapping if exists | Optional component |

## Data Transformation Rules

### 1. Material Number Transformation

**ECC Format:** 18-digit with leading zeros (e.g., `000000000000FG001`)

**Public Cloud Format:** Remove leading zeros (e.g., `FG001`)

```
IF LENGTH(MATNR) > 0 THEN
    Material = LTRIM(MATNR, '0')
END IF
```

### 2. Date Format Transformation

**ECC Format:** SAP Date (YYYYMMDD) as string (e.g., `20240101`)

**Public Cloud Format:** ISO Date (YYYY-MM-DD) (e.g., `2024-01-01`)

```
IF DATUV IS NOT NULL AND DATUV != '00000000' THEN
    ValidityStartDate = SUBSTRING(DATUV, 1, 4) + '-' + SUBSTRING(DATUV, 5, 2) + '-' + SUBSTRING(DATUV, 7, 2)
ELSE
    ValidityStartDate = '' (leave blank for current date)
END IF
```

### 3. Quantity and Decimal Handling

**Rule:** Preserve decimal precision, use period (.) as decimal separator

```
BOMItemQuantity = FORMAT(MENGE, '0.000')
```

### 4. Item Number Formatting

**ECC Format:** 4-digit string with leading zeros (e.g., `0010`)

**Public Cloud Format:** Same format required (e.g., `0010`)

```
BOMItemNumber = RIGHT('0000' + POSNR, 4)
```

### 5. Item Category Code Mapping

| ECC Code (POSTP) | Description | Public Cloud Code | Notes |
|------------------|-------------|-------------------|-------|
| L | Stock item | L | Standard component |
| N | Non-stock item | N | Services, non-valuated |
| T | Text item | T | Documentation only |
| D | Document item | D | Reference documents |
| V | Variable size item | V | Configurable |

### 6. BOM Usage Mapping

| ECC Code (STLAN) | Description | Public Cloud Code |
|------------------|-------------|-------------------|
| 1 | Production | 1 |
| 2 | Engineering/Design | 2 |
| 3 | Plant Maintenance | 3 |
| 5 | Costing | 5 |

### 7. Unit of Measure (UOM) Mapping

Most UOMs map directly, but verify these common ones:

| ECC Code | Description | Public Cloud Code |
|----------|-------------|-------------------|
| EA | Each | EA |
| KG | Kilogram | KG |
| L | Liter | L |
| M | Meter | M |
| PC | Piece | PC |
| ST | Set | ST |

## Template Structure Example

### Excel Template Layout

**Sheet 1: BOM_Header**

```
| Material | Plant | BOMUsage | AlternativeBOM | BOMHeaderBaseUnit | BOMHeaderQuantity | ValidityStartDate |
|----------|-------|----------|----------------|-------------------|-------------------|-------------------|
| FG001    | 1000  | 1        | 01             | EA                | 1.000             | 2024-01-01        |
```

**Sheet 2: BOM_Items**

```
| Material | Plant | BOMUsage | AlternativeBOM | BOMItemNumber | BOMItemComponent | BOMItemQuantity | BOMItemUnit | ComponentScrapPercent |
|----------|-------|----------|----------------|---------------|------------------|-----------------|-------------|-----------------------|
| FG001    | 1000  | 1        | 01             | 0010          | RM001            | 2.500           | KG          | 5                     |
| FG001    | 1000  | 1        | 01             | 0020          | RM002            | 1.000           | L           | 0                     |
```

## Sample Filled Template with Annotations

### Complete BOM Example

**Parent Material:** FG001 - Finished Product Alpha  
**Plant:** 1000 - Main Production Plant

#### BOM Header

```
Material: FG001
  └─ Transformation: Removed leading zeros from 000000000000FG001
Plant: 1000
  └─ Direct mapping from MAST.WERKS
BOMUsage: 1
  └─ Production BOM (MAST.STLAN = '1')
AlternativeBOM: 01
  └─ Primary alternative (MAST.STLAL)
BOMHeaderBaseUnit: EA
  └─ Each (STKO.BMEIN)
BOMHeaderQuantity: 1.000
  └─ Base quantity (STKO.BMENG)
ValidityStartDate: 2024-01-01
  └─ Converted from 20240101 (STKO.DATUV)
```

#### BOM Items

**Item 1:**
```
BOMItemNumber: 0010
  └─ Formatted from STPO.POSNR
BOMItemComponent: RM001
  └─ Raw Material 1, leading zeros removed
BOMItemQuantity: 2.500
  └─ Requires 2.5 kg per 1 EA of FG001
BOMItemUnit: KG
  └─ Kilogram (STPO.MEINS)
ComponentScrapPercent: 5
  └─ 5% scrap factor (STPO.AUSCH)
```

**Item 2:**
```
BOMItemNumber: 0020
BOMItemComponent: RM002
  └─ Raw Material 2
BOMItemQuantity: 1.000
  └─ Requires 1 liter per 1 EA of FG001
BOMItemUnit: L
  └─ Liter (STPO.MEINS)
ComponentScrapPercent: 0
  └─ No scrap (liquid material)
```

## Lookup Value Reference Tables

### BOM Status Codes

| ECC Status (STLST) | Description | Action |
|--------------------|-------------|--------|
| 01 | Active | Migrate |
| 02 | Inactive | Review - migrate only if needed |
| 03 | Locked | Do not migrate |

### Item Category Details

| Category | Can be Purchased | Can be Manufactured | Inventory Relevant |
|----------|------------------|---------------------|-------------------|
| L | Yes | Yes | Yes |
| N | No | No | No |
| T | N/A | N/A | No |

## Common Mapping Issues and Solutions

### Issue 1: Missing Component Materials
**Problem:** Component material doesn't exist in target system  
**Solution:** Create placeholder mapping table or pre-create materials

### Issue 2: Invalid UOM
**Problem:** Source UOM not available in target  
**Solution:** Use UOM conversion table, default to base UOM

### Issue 3: Expired Dates
**Problem:** ValidityEndDate is in the past  
**Solution:** Update to 9999-12-31 or current date + 5 years

### Issue 4: Special Characters in Text Fields
**Problem:** Special characters causing import errors  
**Solution:** Remove or replace: `"`, `'`, `,`, `;`, `|`

## Validation Before Template Creation

Run this checklist:

- [ ] All parent materials exist in target system
- [ ] All component materials exist in target system  
- [ ] All plants are valid in target system
- [ ] All UOMs are valid in target system
- [ ] No duplicate BOM item numbers within same BOM
- [ ] All quantities are positive numbers
- [ ] Date formats are correct (YYYY-MM-DD)
- [ ] Required fields are populated
- [ ] No special characters in key fields

## Notes

- Always validate template against latest SAP Public Cloud documentation
- Template structure may vary based on Public Cloud version
- Consult with SAP Public Cloud implementation partner for exact template format
- Test with small dataset (5-10 BOMs) before full migration

