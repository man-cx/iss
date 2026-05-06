# SAP Migration Validation Framework - Technical Architecture

**Document Version**: 1.0  
**Date**: November 2025  
**Project**: Home Control SAP S/4HANA Migration

## Architecture Overview

The validation framework follows a layered architecture with clear separation of concerns:

```
┌───────────────────────────────────────────────────────────────┐
│                    PRESENTATION LAYER                          │
│  - Command Line Interface (main.py)                           │
│  - Excel Report Output (multi-tab workbooks)                  │
└────────────────────┬──────────────────────────────────────────┘
                     │
┌────────────────────┴──────────────────────────────────────────┐
│                    APPLICATION LAYER                           │
│  - Object-Specific Validators (wave1-4/)                      │
│  - Orchestration Logic                                        │
└────────────────────┬──────────────────────────────────────────┘
                     │
┌────────────────────┴──────────────────────────────────────────┐
│                    BUSINESS LOGIC LAYER                        │
│  - Validator Base Class (ValidatorBase)                       │
│  - Validation Rules Library (ValidationRules)                 │
│  - Result Tracking (ValidationResults)                        │
└────────────────────┬──────────────────────────────────────────┘
                     │
┌────────────────────┴──────────────────────────────────────────┐
│                    DATA ACCESS LAYER                           │
│  - Template Reader (TemplateReader)                           │
│  - Reference Data Loader                                      │
│  - SAP Format Parser                                          │
└────────────────────┬──────────────────────────────────────────┘
                     │
┌────────────────────┴──────────────────────────────────────────┐
│                    INFRASTRUCTURE LAYER                        │
│  - File System (CSV/Excel files)                             │
│  - Configuration (YAML files)                                 │
│  - Logging (Python logging)                                   │
└───────────────────────────────────────────────────────────────┘
```

## Component Details

### 1. Template Reader (`core/template_reader.py`)

**Responsibilities**:
- Read SAP Migration Cockpit templates (CSV and Excel)
- Parse SAP-specific formats (dates, amounts, leading zeros)
- Load and cache reference/master data
- Provide lookup functionality

**Key Classes**:
```python
class TemplateReader:
    - read_template(file_path) -> DataFrame
    - load_reference_data(name, file_path, key_field)
    - lookup_value(reference_name, key_value) -> bool
    - _parse_sap_formats(df) -> DataFrame
```

**Data Flow**:
```
SAP Template File (CSV/Excel)
    → read_template()
    → _read_csv() / _read_excel()
    → _parse_sap_formats()
    → DataFrame with standardized types
```

### 2. Validator Base (`core/validator_base.py`)

**Responsibilities**:
- Provide base class for all validators
- Track validation results with severity levels
- Collect error details and context
- Calculate statistics

**Key Classes**:
```python
class Severity(Enum):
    CRITICAL, HIGH, MEDIUM, LOW, INFO

class ValidationStatus(Enum):
    PASS, FAIL, WARNING, INFO

@dataclass
class ValidationResult:
    row_number, rule_name, field_name, status, severity, message, 
    actual_value, expected_value, context_data, timestamp

class ValidationResults:
    - add_result(result)
    - get_statistics() -> Dict
    - get_errors() -> List[ValidationResult]
    - get_critical_errors() -> List[ValidationResult]
    - has_critical_errors() -> bool
    - to_dataframe() -> DataFrame

class ValidatorBase:
    - load_data(file_path) -> DataFrame
    - validate() -> ValidationResults  # Override in subclasses
    - add_result(...)
    - validate_required_fields(fields, severity)
    - validate_numeric_fields(fields, severity)
    - validate_date_fields(fields, severity)
    - validate_no_duplicates(key_fields, severity)
    - finalize_validation()
```

**Validation Flow**:
```
1. load_data() → Load template into DataFrame
2. validate() → Execute all validation rules
    ├─ Data Quality validations
    ├─ Master Data lookups
    ├─ Business Logic checks
    └─ Reconciliation validations
3. finalize_validation() → Calculate stats, log summary
4. Return ValidationResults
```

### 3. Validation Rules (`core/validation_rules.py`)

**Responsibilities**:
- Provide reusable validation functions
- Implement common business logic
- Support all validation patterns

**Key Functions**:
```python
class ValidationRules:
    # Lookup validations
    - validate_lookup(value, reference_name, template_reader)
    
    # Formula validations
    - validate_formula(row, formula_fields, expected_field, tolerance)
    
    # Value validations
    - validate_positive_value(value, field_name)
    - validate_value_range(value, field_name, min, max)
    
    # Date validations
    - validate_date_range(value, field_name, min_years, max_years)
    - validate_date_sequence(start_date, end_date, field_names)
    
    # Price validations
    - validate_price_reasonableness(net_value, quantity, expected_range)
    - validate_currency_code(code, valid_currencies)
    
    # Financial validations
    - validate_balance_equation(debit, credit, tolerance)
    
    # Reconciliation
    - calculate_reconciliation(data, dimension_field, value_field)
    
    # String validations
    - validate_length(value, field_name, min_length, max_length)
```

**Return Pattern**: All validation functions return:
```python
Tuple[ValidationStatus, str, Optional[Any]]
# (status, message, calculated_value)
```

### 4. Report Generator (`core/report_generator.py`)

**Responsibilities**:
- Generate professional Excel reports
- Create multiple tabs with specific purposes
- Apply conditional formatting
- Add charts and summaries

**Key Methods**:
```python
class ReportGenerator:
    - generate_report(validation_results, output_path, reconciliation_data)
    - _create_summary_tab()      # Executive summary with statistics
    - _create_errors_tab()        # Critical errors with red formatting
    - _create_warnings_tab()      # Warnings with yellow formatting
    - _create_reconciliation_tab()  # Totals and breakdowns
    - _create_detailed_log_tab()  # Full validation log
    - _apply_advanced_formatting()  # Charts and conditional formatting
```

**Report Structure**:
```
Excel Workbook (.xlsx)
├─ Tab 1: Executive Summary
│    ├─ Overall Statistics
│    ├─ Error Counts by Severity
│    ├─ PASS/FAIL Status
│    └─ Sign-Off Section
├─ Tab 2: Critical Errors
│    └─ Filterable table with red highlighting
├─ Tab 3: Warnings
│    └─ Filterable table with yellow highlighting
├─ Tab 4: Reconciliation Summary
│    ├─ Total Counts and Values
│    └─ Breakdowns by Dimensions
└─ Tab 5: Detailed Log
     └─ All validations with color coding
```

### 5. Object Validators (`wave1-4/`)

**Structure**:
```
wave1/
├─ obj01_chart_of_accounts.py
├─ obj03_gl_accounts.py
└─ ...

wave2/
├─ obj15_vendors.py
├─ obj16_customers.py
├─ obj17_materials.py
└─ ...

wave3/
├─ obj25_gl_balances.py
├─ obj27_ap_open_items.py
├─ obj35_sales_orders.py  ← PILOT IMPLEMENTATION
└─ ...

wave4/
├─ obj37_co_planning.py
└─ ...
```

**Pattern**: Each validator:
```python
class ObjectValidator(ValidatorBase):
    # Class constants
    EXPECTED_FIELDS = [...]
    REQUIRED_FIELDS = [...]
    NUMERIC_FIELDS = [...]
    DATE_FIELDS = [...]
    KEY_FIELDS = [...]
    
    def __init__(self, template_reader):
        super().__init__(object_id, object_name, template_reader)
    
    def validate(self) -> ValidationResults:
        # Phase 1: Data Quality
        self.validate_required_fields(...)
        self.validate_numeric_fields(...)
        self.validate_date_fields(...)
        self.validate_no_duplicates(...)
        
        # Phase 2: Master Data
        self._validate_master_data_existence()
        
        # Phase 3: Business Logic
        self._validate_business_rules()
        
        # Phase 4: Reconciliation
        self._perform_reconciliation()
        
        # Finalize
        self.finalize_validation()
        return self.results
    
    def _validate_master_data_existence(self):
        # Object-specific lookups
        ...
    
    def _validate_business_rules(self):
        # Object-specific business logic
        ...
    
    def _perform_reconciliation(self):
        # Object-specific reconciliation
        ...
```

## Configuration System

### Configuration Files

```
src/config/
├─ validation_config.yaml    # Validation rules per object
├─ object_catalog.yaml        # Metadata for all 39 objects
└─ reference_data.yaml        # Reference data locations (optional)
```

### validation_config.yaml Structure

```yaml
object_35_sales_orders:
  object_id: 35
  required_fields: [VBELN, POSNR, KUNNR, ...]
  numeric_fields: [KWMENG, LFIMG, ...]
  date_fields: [ERDAT, EDATU]
  
  validations:
    - rule: "customer_exists"
      type: "lookup"
      field: "KUNNR"
      reference_table: "customer_master"
      severity: "critical"
      message: "Customer {KUNNR} does not exist"
    
    - rule: "open_quantity_calculation"
      type: "formula"
      formula: "KWMENG - LFIMG"
      expected_field: "OPEN_QTY"
      tolerance: 0.001
      severity: "high"
```

### object_catalog.yaml Structure

```yaml
objects:
  - id: 35
    name: "Open Sales Orders"
    wave: 3
    template_file: "SD_SALES_ORDER.xlsx"
    key_fields: ["VBELN", "POSNR"]
    functional_lead: "SD Lead"
    dependencies: ["obj16_customers", "obj17_materials"]
    priority: "High"
    criticality: "operational"
    validator_class: "SalesOrderValidator"
    validator_module: "wave3.obj35_sales_orders"
```

## Data Flow

### End-to-End Validation Flow

```
┌─────────────────┐
│ User invokes    │
│ main.py         │
│ --object 35     │
└────────┬────────┘
         │
         ▼
┌────────────────────────────┐
│ Main Entry Point           │
│ - Parse arguments          │
│ - Initialize components    │
└────────┬───────────────────┘
         │
         ▼
┌────────────────────────────┐
│ Template Reader            │
│ - Load input file          │
│ - Load reference data      │
│ - Parse SAP formats        │
└────────┬───────────────────┘
         │
         ▼
┌────────────────────────────┐
│ Object Validator           │
│ - Execute validation rules │
│ - Collect results          │
└────────┬───────────────────┘
         │
         ▼
┌────────────────────────────┐
│ Report Generator           │
│ - Create Excel report      │
│ - Apply formatting         │
└────────┬───────────────────┘
         │
         ▼
┌────────────────────────────┐
│ Output Excel File          │
│ - 5 tabs                   │
│ - Ready for sign-off       │
└────────────────────────────┘
```

## Technology Stack

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Language** | Python 3.8+ | Main programming language |
| **Data Processing** | pandas | DataFrame operations |
| **Excel Reading** | openpyxl | Read Excel files |
| **Excel Writing** | xlsxwriter | Write Excel with formatting |
| **Configuration** | pyyaml | YAML configuration files |
| **Testing** | pytest | Unit testing framework |
| **Logging** | Python logging | Audit trail and debugging |

## Performance Considerations

### Optimization Strategies

1. **Reference Data Caching**:
   - Load reference data once at startup
   - Index by key field for O(1) lookup
   - Keep in memory for duration of validation

2. **Batch Processing**:
   - Process large files in chunks if needed
   - Default: Load entire file (up to 100K records)

3. **Parallel Processing** (Future):
   - Validate multiple objects in parallel
   - Use multiprocessing for large files

### Performance Targets

| Object | Records | Time Target | Actual |
|--------|---------|-------------|--------|
| Object 35 (SO) | 1,000 | < 30 seconds | ✅ ~15 seconds |
| Object 35 (SO) | 10,000 | < 60 seconds | (To be tested) |
| Object 27 (AP) | 5,000 | < 45 seconds | (To be implemented) |

## Extensibility

### Adding a New Object

**Steps** (2-4 hours):

1. Create validator file: `wave#/obj##_object_name.py`
2. Inherit from `ValidatorBase`
3. Implement `validate()` method
4. Add entry to `object_catalog.yaml`
5. Update `main.py` to route to new validator
6. Create sample data for testing
7. Test and document

### Adding a New Validation Rule

**Steps** (1-2 hours):

1. Add function to `validation_rules.py` if reusable
2. Or implement in object-specific validator
3. Call from `validate()` method
4. Add to `validation_config.yaml`
5. Document in `validation_catalog.md`
6. Test with sample data

## Security Considerations

1. **File Access**: Framework reads only CSV/Excel files
2. **No Network Access**: All operations are local
3. **No Database Access**: File-based only
4. **Audit Trail**: All validations logged to file
5. **Read-Only on Templates**: Original files not modified

## Error Handling

### Error Categories

1. **User Errors**:
   - File not found → Clear message with file path
   - Invalid file format → Suggest correct format
   - Missing reference data → List required files

2. **Data Errors**:
   - Validation failures → Captured in results
   - Parse errors → Logged with row number

3. **System Errors**:
   - Memory errors → Suggest chunked processing
   - Disk errors → Check file permissions

### Logging Levels

- **DEBUG**: Detailed validation progress
- **INFO**: High-level progress, statistics
- **WARNING**: Non-critical issues (e.g., reference data not found)
- **ERROR**: Critical failures that prevent validation

## Future Enhancements

### Phase 2 (Post-Pilot)

1. Post-import validation (ECC vs S/4HANA comparison)
2. Parallel validation for multiple objects
3. Web UI for report viewing
4. Real-time validation dashboard

### Phase 3 (Post Go-Live)

1. Auto-fix capabilities for common errors
2. Machine learning for anomaly detection
3. Integration with SAP system for direct validation
4. Historical trending and analytics

## Related Documents

- [User Guide](../../sap-migration-validator/docs/user_guide.md)
- [Developer Guide](../../sap-migration-validator/docs/developer_guide.md)
- [Validation Catalog](../../sap-migration-validator/docs/validation_catalog.md)
- [Framework Overview](validation-framework-overview.md)

