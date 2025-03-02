# Naming Convention
Snake case (most preferred)
Do not use SQL reserved words as object names

# Bronze Rules

All names must start with the source system name, and table names must match their original names without renaming.
<sourcesystem>_<entity>
    <sourcesystem>: Name of the source system (e.g., crm, erp).
    <entity>: Exact table name from the source system.

Example: crm_customer_info → Customer information from the CRM system.

# Silver Rules

All names must start with the source system name, and table names must match their original names without renaming.
<sourcesystem>_<entity>
    <sourcesystem>: Name of the source system (e.g., crm, erp).
    <entity>: Exact table name from the source system.

Example: crm_customer_info → Customer information from the CRM system.

# Gold Rules

All names must use meaningful, business-aligned names for tables, starting with the category prefix.
<category>_<entity>
    <category>: Describes the role of the table, such as dim (dimension) or fact (fact table).
    <entity>: Descriptive name of the table, aligned with the business domain (e.g., customers, products, sales).

Examples:
dim_customers → Dimension table for customer data.
fact_sales → Fact table containing sales transactions.

# Glossary of Category Patterns

| Pattern   | Meaning        | Example(s)|
|-----------|----------------|-----------|
| dim_      | Dimension table| dim_customer, dim_product    |
| fact_     | Fact table     | fact_sales    |
| report_   | Report table   | report_customers, report_sales_monthly    |


# Surrogate Keys

1. All primary keys in dimension tables must use the suffix _key.
2. <table_name>_key
    <table_name>: Refers to the name of the table or entity the key belongs to.
    _key: A suffix indicating that this column is a surrogate key.
    Example: customer_key → Surrogate key in the dim_customers table.

# Technical Columns

1. All technical columns must start with the prefix dwh_, followed by a descriptive name indicating the column's purpose.
2. dwh_<column_name>
    dwh: Prefix exclusively for system-generated metadata.
    <column_name>: Descriptive name indicating the column's purpose.

Example: dwh_load_date → System-generated column used to store the date when the record was loaded.

# Stored Procedure

All stored procedures used for loading data must follow the naming pattern:

load_<layer>.

<layer>: Represents the layer being loaded, such as bronze, silver, or gold.
    Example:
    load_bronze → Stored procedure for loading data into the Bronze layer.
    load_silver → Stored procedure for loading data into the Silver layer.

# Analyzing Bronze Layer
1. Analyzing - Interview source systems expert
2. Coding - Data Ingestion
3. Validating - Data Completeness and Schema Checks
4. Docs & Version - Data Documenting and Versioning in Git

Questions
1. Who owns the data?
2. What business process it supports? --> does it support the customer transactions, the supply chain Logistics or maybe finance reporting
3. System and Data Documentation
4. Data Model for the source system and if they have description of the columns and tables, it is going to be nice to have the data catalog, this can help me a lot in the DW and how am i going to join the tables
5. Architecture and Technology Stack
    a. How is data stored?
    b. What are the integration capabilities? 
6. Extract & Load
    a. Incremental vs full load
    b. Data scope and historical needs - need all data, need any history, timeline
    c. Expected size of the extracts
    d. Are there any volumn limitations?
    e. how to avoid impacting the source systems performance?
    f. authentication vs authorization