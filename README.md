# data-warehousing
Data Warehousing practice

# Intro
DataWarehouse - - > A subject oriented (focussed on business area like sales, customer, finance etc), time-variant (ex. historical data), integrated (integrate multiple source systems), and non-volatile (not deleted or not modified) collection of data in support of management's decision making process.

# Why do we need a data warehouse?
From my experience, managing data without a Data Warehouse is chaos. Teams pull reports from different systems—and end up with conflicting numbers, outdated reports, and endless manual work.

A Data Warehouse fixes this:

    Centralized Data: All in one place.
    Automation: ETL pipelines handle cleaning and loading.
    Consistency: One source of truth.
    Speed: Reports ready in hours, not weeks.

# ETL

1. Extract - we pull the required data from the system; just identifying the data we need, we pull it out and we don't do anything (means we do not manipulate data)
2. Transformation - manipulations, Transformation, change the shape of extracted data, data cleansing, data integration, formatting, data normalization
3. Load - move to its final destination (load to its target table)

# Extraction
## Methods

1. Pull Extraction - you go to source system and pull the data from the source
2. Push Extraction - the source system pushing the data to the data warehouse

## Types

1. Full Extraction - extract everything; all the records from the table; we load all the data to the data warehouse
2. Incremental Extraction - identify the new changing data and load to data warehouse (smarter choice)

## Techniques

1. Manual Data Extraction - someone access the source system and extract the data manually
2. Database Querying - connect ourself to a database and a query in order to extract the data
3. File Parsing - file parse to datawarehouse
4. API calls - connect to API
5. Event Based Streaming - kafka streaming
6. CDC -  Change data capture very similar to streaming
7. Web Scraping - by using web


# Transformation
1. Data Enrichment - where we add values to our data set
2. Data Intergration - where we have multiple sources and we bring to one data model
3. Derived Columns - where we derive new columns based on the existing ones
4. Data Normalization and Standardization - sources that have code need mapping to a friendlier values for the analysis
5. Business Rules and Logic - based on business logic, you can create new columns
6. Data Aggregations - aggregate data to a different granularity
7. Data Cleansing:
    a. Remove Duplicates
    b. Data Filtering
    c. Handling Missing Data
    d. Handling Invalid Values
    e. Handling Unwanted Spaces
    f. Data Type Casting 
    g. Outlier Detection

# Loading
## Processing Type
1. Batch Processing - big batch of data; scheduling the data warehouse
2. Stream Processing - processing the change in source system as soon as possible to have real time data warehouse; streaming has some challenges

## Methods
1. Full Load
    a. Truncate & Insert - we make the table empty and then insert everything from scratch
    b. Upsert - update the existing records or insert new records
    c. Drop, Create, Insert - we drop, create from scratch and insert new records

2. Incremental Load
    a. Upsert - update the existing records or insert new records
    b. Append - insert only
    c. Merge - similar to upsert, but it deletes also

## SCD - Slowly Changing Dimension
    a. SCD 0 - No change at all
    b. SCD 1 - Overwrite
    c. SCD 2 - Maintain History
    d. SCD 3 - new and previous value maintained

