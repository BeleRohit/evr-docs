6. Our "Metadata" Tables: The Pipeline's Brains 🧠
Our data pipeline is smart because it's driven by metadata { data-tooltip="Data about data: Information stored in special tables that describes our files, columns, and the rules for processing them." }. This "data about data" tells our systems how to handle different files, what columns they have, and what transformations to apply. This metadata is stored in special tables within our Snowflake { data-tooltip="Our powerful cloud-based data warehouse. This is where most of our processed data lives and where our analytical tools connect." } data warehouse.

These tables are crucial because they make our pipeline flexible. Instead of hardcoding rules into every script, we define them once in these tables, and our pipeline reads from them dynamically.

Here are some of the most important metadata tables you'll hear about:

DYNAMIC_DATA_LOADS:

Purpose: This table holds all the instructions for how we load raw data.

What it defines: It tells the pipeline things like the unique ID for a file (FILE ID), where the file is located in AWS S3 (S3 FILE PATH), how often we expect to receive it (FREQUENCY - daily, weekly), and the specific type of initial load (RAW LOAD_TYPE - e.g., "FIRST_TIME" for a new dataset, or "TRUNCATE" which means replacing all old data with new).

Example Query:

SELECT "FILE ID", "S3 FILE PATH", "FREQUENCY", "RAW LOAD_TYPE"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_DATA_LOADS
LIMIT 5;

DYNAMIC_COLUMN_DEFINITIONS:

Purpose: This table is like a dictionary for our data columns. It defines the structure and data type for every column in our tables.

What it defines: For each TABLE IDENTIFIER, it specifies the COLUMN NAME, what kind of data it should hold (DATATYPE - e.g., TEXT for words, FIXED for numbers, DATE for dates), and sometimes even custom rules for transforming the column's values (COLUMN_VALUE_TRANSFORMATION).

Example Query:

SELECT "TABLE IDENTIFIER", "COLUMN NAME", "DATATYPE", "COLUMN_VALUE_TRANSFORMATION"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_COLUMN_DEFINITIONS
WHERE "TABLE IDENTIFIER" = 'YOUR_EXAMPLE_TABLE'
LIMIT 5;

DYNAMIC_CORE_LOADS:

Purpose: This table contains the rules for how we process data in our Core Layer (where the main cleaning and transformation happens).

What it defines: It specifies the type of load for the Core Layer (CORE LOAD TYPE - e.g., "DELTA" for incremental updates, "UPSERT" for merging new and existing data), and important flags like ENRICHMENT FLAG which tells the pipeline if additional "enrichment" steps are needed for the data.

Example Query:

SELECT "TABLE IDENTIFIER", "CORE LOAD TYPE", "ENRICHMENT FLAG"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_CORE_LOADS
LIMIT 5;

DYNAMIC_FTB_INPUT_UNIVERSE:

Purpose: This table tracks the status of every incoming input file as it moves through each stage of the pipeline.

What it defines: It records the file's ID, name, S3 path, and the status of various checks (e.g., "pre-validation successful," "raw load complete," "core load failed," "data quality monitoring run"). This is crucial for troubleshooting if a file gets stuck or an error occurs.

Example Query:

SELECT "FILE ID", "FILE NAME", "PRE VALIDATION", "CORE LOAD", "ERROR"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_FTB_INPUT_UNIVERSE
ORDER BY "SYSTEM DATE" DESC
LIMIT 5;

DYNAMIC_ENRICHMENT_LOADS:

Purpose: This table stores special SQL queries that are run to "enrich" our data. Enrichment means adding more value or detail to existing data (e.g., looking up customer demographics based on an ID).

What it defines: It links a specific file and table to a custom SQL_QUERY that will perform the enrichment operation.

Example Query:

SELECT "TABLE_IDENTIFIER", "SQL_QUERY"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_ENRICHMENT_LOADS
WHERE "TABLE_IDENTIFIER" = 'YOUR_ENRICHMENT_TABLE'
LIMIT 1;

Potential Improvements for this Section:
Simple SQL Examples: For each metadata table, provide a very basic SQL SELECT statement that a new user could run in Snowflake to see what kind of data is in that table.

Relationship Between Tables: Briefly explain how these tables relate to each other (e.g., "The FILE ID in DYNAMIC_DATA_LOADS connects to the FILE ID in DYNAMIC_ENRICHMENT_LOADS").

"Why Metadata?" Explanation: Briefly explain why we use metadata tables (e.g., "to make our pipeline flexible," "to avoid hardcoding rules").