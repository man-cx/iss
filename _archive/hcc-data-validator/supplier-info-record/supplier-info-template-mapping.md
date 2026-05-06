# Supplier Info Record Template Mapping Guide

## Overview
This guide provides detailed field-by-field mapping from SAP ECC 6.0 tables to SAP ERP Public Cloud import templates for Supplier Info Record migration.

## Template Structure

SAP ERP Public Cloud uses standardized import templates for supplier info records. The template typically consists of one or two sheets depending on pricing data:

- **Sheet 1:** Supplier Info Record (Main Data)
- **Sheet 2:** Supplier Info Record Pricing (Optional - if using separate pricing upload)

## Field Mapping: Main Supplier Info Record

### Template Column Structure

The Public Cloud import template typically has these columns (verify with your specific template):

| Column | Field Name | Required | Data Type | Max Length |
|--------|------------|----------|-----------|------------|
| A | Vendor | Yes | Alphanumeric | 10 |
| B | Material | Yes | Alphanumeric | 40 |
| C | PurchasingOrganization | Yes | Alphanumeric | 4 |
| D | Plant | No | Alphanumeric | 4 |
| E | InfoRecordCategory | No | Alphanumeric | 1 |
| F | OrderUnit | Yes | Alphanumeric | 3 |
| G | StandardQuantity | No | Decimal | - |
| H | PlannedDeliveryTime | No | Integer | - |
| I | PurchasingGroup | No | Alphanumeric | 3 |
| J | NetPrice | Yes | Decimal | - |
| K | PriceUnit | Yes | Integer | - |
| L | Currency | Yes | Alphanumeric | 3 |
| M | PriceDate | No | Date | - |
| N | TaxCode | No | Alphanumeric | 2 |
| O | MinimumOrderQuantity | No | Decimal | - |
| P | MaximumOrderQuantity | No | Decimal | - |
| Q | IncotermsLocation1 | No | Alphanumeric | 3 |
| R | IncotermsLocation2 | No | Alphanumeric | 70 |
| S | OverdeliveryTolerance | No | Decimal | - |
| T | UnderdeliveryTolerance | No | Decimal | - |
| U | GRBasedInvoiceVerification | No | Boolean | - |
| V | VendorSubrange | No | Alphanumeric | 6 |
| W | ReminderDays1 | No | Integer | - |
| X | ReminderDays2 | No | Integer | - |
| Y | ReminderDays3 | No | Integer | - |

**Note:** The exact column order and names may vary by Public Cloud release. Always verify with your system's template.

## Detailed Field Mappings

### Column A: Vendor
**Source:** `EINA.LIFNR`

**Transformation:**
- Remove leading zeros
- Keep vendor number as 10-character string
- Verify vendor exists in Public Cloud system

**Excel Formula:**
```excel
=TEXT(VALUE([SourceSheet]!A2),"0")
```

**Validation:**
- Must not be blank
- Must exist in vendor master
- Must be active (not blocked)

---

### Column B: Material
**Source:** `EINA.MATNR`

**Transformation:**
- Remove leading zeros
- Keep material number as alphanumeric string
- Verify material exists in Public Cloud system

**Excel Formula:**
```excel
=TEXT(VALUE([SourceSheet]!B2),"0")
```

**Alternative (if material contains alphanumeric characters):**
```excel
=TRIM([SourceSheet]!B2)
```

**Validation:**
- Must not be blank
- Must exist in material master
- Material must be flagged for purchasing

---

### Column C: PurchasingOrganization
**Source:** `EINE.EKORG`

**Transformation:**
- Direct mapping (usually 4 characters)
- Verify purchasing org exists in Public Cloud

**Excel Formula:**
```excel
=[SourceSheet]!C2
```

**Validation:**
- Must not be blank
- Must exist in organizational structure
- Must be active

---

### Column D: Plant
**Source:** `EINE.WERKS`

**Transformation:**
- Direct mapping (usually 4 characters)
- Can be blank for non-plant-specific info records
- Verify plant exists in Public Cloud

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!D2),"",[SourceSheet]!D2)
```

**Validation:**
- Can be blank
- If populated, must exist in plant master
- Must be assigned to the purchasing organization

---

### Column E: InfoRecordCategory
**Source:** `EINE.ESOKZ`

**Transformation:**
- Direct mapping
- Usually blank, "0" (standard), or "2" (sub-range)

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!E2),"0",[SourceSheet]!E2)
```

**Validation:**
- Default to "0" if blank
- Valid values: 0, 1, 2 (check your system)

---

### Column F: OrderUnit
**Source:** `EINA.MEINS`

**Transformation:**
- Direct mapping
- Ensure unit of measure exists in Public Cloud
- Common values: EA, PC, KG, LB, M, FT

**Excel Formula:**
```excel
=[SourceSheet]!F2
```

**Validation:**
- Must not be blank
- Must exist in UoM master
- Should match material base unit or alternate units

---

### Column G: StandardQuantity
**Source:** `EINE.NORBM`

**Transformation:**
- Format as decimal with 3 decimal places
- Can be blank if not used

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!G2),"",TEXT([SourceSheet]!G2,"0.000"))
```

**Validation:**
- Must be positive if populated
- Typically used for lot size calculations

---

### Column H: PlannedDeliveryTime
**Source:** `EINE.APLFZ`

**Transformation:**
- Direct mapping (integer, number of days)
- Critical for MRP calculations

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!H2),0,VALUE([SourceSheet]!H2))
```

**Validation:**
- Must be numeric
- Typically 0-365 days
- Zero is acceptable

---

### Column I: PurchasingGroup
**Source:** `EINE.EKGRP`

**Transformation:**
- Direct mapping (3 characters)
- Verify purchasing group exists in Public Cloud

**Excel Formula:**
```excel
=[SourceSheet]!I2
```

**Validation:**
- Can be blank
- If populated, must exist in purchasing group master
- Should be active

---

### Column J: NetPrice
**Source:** `EINE.NETPR`

**Transformation:**
- Format as decimal with 2-5 decimal places (depending on currency)
- Critical field for purchasing
- Alternative source: `KONP.KBETR` (if using condition records)

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!J2),0,TEXT([SourceSheet]!J2,"0.00"))
```

**Validation:**
- Must not be blank
- Must be positive (> 0)
- Should be reasonable for the material

---

### Column K: PriceUnit
**Source:** `EINE.PEINH`

**Transformation:**
- Integer value (typically 1, 10, 100, 1000)
- Indicates the quantity for which the price applies
- Example: Price of $10.00 per 100 units → PriceUnit = 100

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!K2),1,VALUE([SourceSheet]!K2))
```

**Validation:**
- Must not be blank
- Default to 1 if not specified
- Common values: 1, 10, 100, 1000

---

### Column L: Currency
**Source:** `EINE.WAERS`

**Transformation:**
- Direct mapping (3-character ISO code)
- Common values: USD, EUR, GBP, CAD

**Excel Formula:**
```excel
=[SourceSheet]!L2
```

**Validation:**
- Must not be blank
- Must be valid ISO 4217 currency code
- Currency must exist in Public Cloud system

---

### Column M: PriceDate
**Source:** `EINE.PRDAT`

**Transformation:**
- Convert from YYYYMMDD to YYYY-MM-DD format
- Can use current date if blank

**Excel Formula (ECC date is in format YYYYMMDD):**
```excel
=IF(ISBLANK([SourceSheet]!M2),TEXT(TODAY(),"YYYY-MM-DD"),TEXT(DATE(LEFT([SourceSheet]!M2,4),MID([SourceSheet]!M2,5,2),RIGHT([SourceSheet]!M2,2)),"YYYY-MM-DD"))
```

**Validation:**
- Should not be future date
- Should not be too old (> 2 years may need review)

---

### Column N: TaxCode
**Source:** `EINE.MWSKZ`

**Transformation:**
- Direct mapping
- Verify tax code exists in Public Cloud
- Common values: V0, V1, V2, etc.

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!N2),"",[SourceSheet]!N2)
```

**Validation:**
- Can be blank
- If populated, must exist in tax configuration
- Must be valid for the purchasing organization

---

### Column O: MinimumOrderQuantity
**Source:** `EINE.MINBM`

**Transformation:**
- Format as decimal with 3 decimal places
- Can be blank or zero

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!O2),"",TEXT([SourceSheet]!O2,"0.000"))
```

**Validation:**
- If populated, must be positive
- Should be less than or equal to MaximumOrderQuantity

---

### Column P: MaximumOrderQuantity
**Source:** `EINE.BSTMA`

**Transformation:**
- Format as decimal with 3 decimal places
- Can be blank or zero

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!P2),"",TEXT([SourceSheet]!P2,"0.000"))
```

**Validation:**
- If populated, must be positive
- Should be greater than or equal to MinimumOrderQuantity

---

### Column Q: IncotermsLocation1
**Source:** `EINE.INCO1`

**Transformation:**
- Direct mapping (3 characters)
- Common values: FOB, CIF, DDP, EXW, FCA

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!Q2),"",[SourceSheet]!Q2)
```

**Validation:**
- Can be blank
- If populated, must be valid Incoterms code
- Should match organizational standards

---

### Column R: IncotermsLocation2
**Source:** `EINE.INCO2`

**Transformation:**
- Direct mapping (text field)
- Describes location or additional terms

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!R2),"",[SourceSheet]!R2)
```

**Validation:**
- Can be blank
- Free text field
- Should contain location or description

---

### Column S: OverdeliveryTolerance
**Source:** `EINE.UEBTO`

**Transformation:**
- Format as decimal (percentage)
- Example: 10.5 means 10.5% over-delivery allowed

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!S2),"",TEXT([SourceSheet]!S2,"0.0"))
```

**Validation:**
- Can be blank or zero
- Typically 0-100 (percentage)
- Should not exceed system-defined limits

---

### Column T: UnderdeliveryTolerance
**Source:** `EINE.UNTTO`

**Transformation:**
- Format as decimal (percentage)
- Example: 5.0 means 5% under-delivery allowed

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!T2),"",TEXT([SourceSheet]!T2,"0.0"))
```

**Validation:**
- Can be blank or zero
- Typically 0-100 (percentage)
- Should not exceed system-defined limits

---

### Column U: GRBasedInvoiceVerification
**Source:** `EINE.WEBRE`

**Transformation:**
- Convert to Boolean or X/blank
- ECC value: 'X' or blank
- Public Cloud may require: TRUE/FALSE or X/blank

**Excel Formula:**
```excel
=IF([SourceSheet]!U2="X","TRUE","FALSE")
```

**Alternative (if template uses X):**
```excel
=[SourceSheet]!U2
```

**Validation:**
- Must be valid Boolean indicator
- Controls whether invoice can be posted before goods receipt

---

### Column V: VendorSubrange
**Source:** `EINA.LTSNR`

**Transformation:**
- Direct mapping
- Used when vendor has multiple sub-ranges for same material

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!V2),"",[SourceSheet]!V2)
```

**Validation:**
- Can be blank
- Typically used for specific vendor scenarios

---

### Column W: ReminderDays1
**Source:** `EINA.MAHN1`

**Transformation:**
- Direct mapping (integer days)
- First reminder for delivery delays

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!W2),"",VALUE([SourceSheet]!W2))
```

**Validation:**
- Can be blank
- Must be numeric if populated

---

### Column X: ReminderDays2
**Source:** `EINA.MAHN2`

**Transformation:**
- Direct mapping (integer days)
- Second reminder for delivery delays

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!X2),"",VALUE([SourceSheet]!X2))
```

**Validation:**
- Can be blank
- Should be > ReminderDays1

---

### Column Y: ReminderDays3
**Source:** `EINA.MAHN3`

**Transformation:**
- Direct mapping (integer days)
- Third reminder for delivery delays

**Excel Formula:**
```excel
=IF(ISBLANK([SourceSheet]!Y2),"",VALUE([SourceSheet]!Y2))
```

**Validation:**
- Can be blank
- Should be > ReminderDays2

---

## Code Mapping Tables

### Info Record Category (ESOKZ)

| ECC Value | Description | Public Cloud Value |
|-----------|-------------|--------------------|
| 0 | Standard | 0 |
| 1 | Consignment | 1 |
| 2 | Sub-range | 2 |
| (blank) | Standard | 0 |

### Common Tax Codes

| ECC Code | Description | Public Cloud Code | Notes |
|----------|-------------|-------------------|-------|
| V0 | Input Tax 0% | V0 | Non-taxable |
| V1 | Input Tax (Standard) | V1 | Standard VAT/Tax |
| V2 | Input Tax (Reduced) | V2 | Reduced rate |
| ** | (varies by country) | (verify mapping) | Map per country |

**Note:** Tax codes are highly country-specific. Verify mappings with your tax team.

### Common Units of Measure

| ECC UoM | Description | Public Cloud UoM | Notes |
|---------|-------------|------------------|-------|
| EA | Each | EA | Standard |
| PC | Piece | PC | Standard |
| KG | Kilogram | KG | Standard |
| LB | Pound | LB | Standard |
| M | Meter | M | Standard |
| FT | Foot | FT | Standard |
| L | Liter | L | Standard |
| GAL | Gallon | GAL | Standard |

### Common Incoterms

| Incoterms | Description | Valid |
|-----------|-------------|-------|
| EXW | Ex Works | Yes |
| FCA | Free Carrier | Yes |
| FOB | Free On Board | Yes |
| CFR | Cost and Freight | Yes |
| CIF | Cost, Insurance, Freight | Yes |
| DDP | Delivered Duty Paid | Yes |
| DAP | Delivered at Place | Yes |

## Transformation Rules

### Rule 1: Material Number Zero-Padding

**Issue:** ECC stores material numbers with leading zeros, but Public Cloud may not.

**Solution:**
```excel
=TEXT(VALUE(A2),"0")
```

**Example:**
- ECC: `000000012345`
- Public Cloud: `12345`

---

### Rule 2: Vendor Number Zero-Padding

**Issue:** Same as material numbers.

**Solution:**
```excel
=TEXT(VALUE(B2),"0")
```

**Example:**
- ECC: `0001000001`
- Public Cloud: `1000001`

---

### Rule 3: Date Format Conversion

**Issue:** ECC uses YYYYMMDD, Public Cloud uses YYYY-MM-DD.

**Solution:**
```excel
=TEXT(DATE(LEFT(A2,4),MID(A2,5,2),RIGHT(A2,2)),"YYYY-MM-DD")
```

**Example:**
- ECC: `20230515`
- Public Cloud: `2023-05-15`

---

### Rule 4: Price Decimal Formatting

**Issue:** Ensure consistent decimal places for prices.

**Solution:**
```excel
=TEXT(A2,"0.00")
```

**Example:**
- ECC: `25.5`
- Public Cloud: `25.50`

---

### Rule 5: Boolean Field Conversion

**Issue:** ECC uses 'X'/blank, Public Cloud may use TRUE/FALSE.

**Solution:**
```excel
=IF(A2="X","TRUE","FALSE")
```

**Example:**
- ECC: `X`
- Public Cloud: `TRUE`

---

### Rule 6: Handling Blank Fields

**Issue:** Public Cloud may not accept NULL or may require specific default values.

**Solution:**
```excel
=IF(ISBLANK(A2),"[default value]",A2)
```

**Examples:**
- Numeric fields: Default to 0
- Text fields: Default to "" (empty string)
- Required fields: Must not be blank

---

### Rule 7: Currency Code Standardization

**Issue:** Ensure 3-character ISO codes.

**Solution:**
```excel
=UPPER(TRIM(A2))
```

**Validation:** Must be valid ISO 4217 code.

---

### Rule 8: Price Unit Handling

**Issue:** ECC field PEINH may be blank, but Public Cloud requires a value.

**Solution:**
```excel
=IF(ISBLANK(A2),1,A2)
```

**Default:** 1 (price per 1 unit)

---

## Example Template (First 3 Rows)

| Vendor | Material | PurchOrg | Plant | OrderUnit | NetPrice | PriceUnit | Currency | PlannedDeliveryTime |
|--------|----------|----------|-------|-----------|----------|-----------|----------|---------------------|
| 1000001 | 12345 | 1000 | 1000 | EA | 25.50 | 1 | USD | 14 |
| 1000002 | 12346 | 1000 | 1000 | KG | 150.00 | 1 | USD | 21 |
| 1000003 | 12347 | 1000 | 2000 | PC | 5.75 | 10 | EUR | 7 |

## Common Mapping Issues and Solutions

### Issue 1: Duplicate Info Records
**Problem:** Multiple EINE records for same EINA (multiple purchasing orgs or plants).

**Solution:** Create separate rows in template for each unique combination of:
- Vendor + Material + Purchasing Org + Plant

---

### Issue 2: Missing Prices
**Problem:** EINE.NETPR is zero or blank.

**Solution:**
- Check A018/KONP for condition records
- If no pricing found, decide: skip record or use default price
- Document all zero-price records for business review

---

### Issue 3: Invalid Units of Measure
**Problem:** ECC UoM doesn't exist in Public Cloud.

**Solution:**
- Create mapping table for UoM conversion
- Coordinate with master data team to create missing UoMs in Public Cloud
- Use alternate UoM if available

---

### Issue 4: Invalid Vendor/Material
**Problem:** Vendor or material doesn't exist in Public Cloud.

**Solution:**
- Vendor/Material must be migrated first (prerequisite)
- Create dependency list
- Verify all vendors/materials exist before info record migration

---

### Issue 5: Long Text Fields Truncated
**Problem:** Incoterms2 or other text fields exceed max length.

**Solution:**
- Truncate to max length allowed
- Document truncated fields
- Consider using notes/attachments for full text

---

## Validation Rules Summary

1. **Vendor** - Must exist in vendor master, must be active
2. **Material** - Must exist in material master, must be flagged for purchasing
3. **PurchasingOrganization** - Must exist and be active
4. **Plant** - If populated, must exist and be assigned to purchasing org
5. **OrderUnit** - Must exist in UoM master
6. **NetPrice** - Must be positive and non-zero
7. **Currency** - Must be valid ISO 4217 code
8. **PriceUnit** - Must be positive integer
9. **MinOrderQty** - If populated, must be ≤ MaxOrderQty
10. **MaxOrderQty** - If populated, must be ≥ MinOrderQty

## Template Preparation Workflow

1. **Extract data** from ECC using queries from `supplier-info-extraction.md`
2. **Create template file** with Public Cloud column structure
3. **Map columns** using formulas provided in this document
4. **Apply transformations** for dates, numbers, units
5. **Validate** required fields are populated
6. **Check** for duplicates within template
7. **Verify** all vendors and materials exist in Public Cloud
8. **Format** as CSV UTF-8 for upload
9. **Test** with small batch before full import

## Notes

- Always verify template structure with your specific Public Cloud version
- Column names and order may vary by release
- Some fields may be optional in your system that are marked required here (or vice versa)
- Work with your implementation partner to confirm exact template requirements
- Keep a mapping document for custom fields specific to your organization

## Document Version

- **Created:** [Date]
- **Last Updated:** [Date]
- **Project:** SAP ECC 6.0 to SAP ERP Public Cloud Migration
- **Author:** Migration Team


