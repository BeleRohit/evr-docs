# 6. Our *Metadata* Tables: The Pipeline's Brains 🧠

At EVERSANA, our data pipeline is **smart and flexible** because it's **driven by metadata**.

## What is Metadata?

**Metadata** means "**data about data**." In our pipelines, metadata tells the system:

- **What files to load**  
- **Where to find them**  
- **What columns they contain**  
- **What transformations to apply**  
- **How to handle errors or exceptions**

This removes the need to hardcode rules into scripts. Instead, we define rules **once** in metadata tables, and the pipeline reads them **dynamically** at runtime.

All metadata is stored in **Snowflake**, our cloud data warehouse.

---

## Why Use Metadata?

| Benefit                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| **Flexibility**                        | New files and columns can be added without rewriting code. |
| **Reusability**                        | Same pipeline logic works for multiple datasets. |
| **Transparency**                      | Clear documentation of how data is processed. |
| **Error Reduction**                    | Fewer manual code changes = fewer bugs.       |
| **Simplified Troubleshooting**         | Metadata tracks file status and process flows.|

---

## Key Metadata Tables in Our Pipeline

Below are the most important metadata tables you'll encounter:



### **1️⃣ DYNAMIC_DATA_LOADS**

#### **Purpose:**  
Stores instructions for how **raw data is loaded** into the system.

#### **What it Defines:**

| Column              | Description                                           |
|--------------------|-------------------------------------------------------|
| `FILE ID`           | Unique identifier for each input file                |
| `S3 FILE PATH`      | AWS S3 location of the file                          |
| `FREQUENCY`         | How often we expect the file (e.g., Daily, Weekly)  |
| `RAW LOAD_TYPE`     | Loading method (e.g., `FIRST_TIME`, `TRUNCATE`)     |

#### **Example Query:**

```sql
SELECT "FILE ID", "S3 FILE PATH", "FREQUENCY", "RAW LOAD_TYPE"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_DATA_LOADS
LIMIT 5;
````

---

### **2️⃣ DYNAMIC\_COLUMN\_DEFINITIONS**

#### **Purpose:**

Acts as a **data dictionary** for every table and file column in our pipeline.

#### **What it Defines:**

| Column                        | Description                                   |
| ----------------------------- | --------------------------------------------- |
| `TABLE IDENTIFIER`            | The name of the table or dataset              |
| `COLUMN NAME`                 | The name of each column                       |
| `DATATYPE`                    | The data type (`TEXT`, `FIXED`, `DATE`, etc.) |
| `COLUMN_VALUE_TRANSFORMATION` | Custom rules for transforming column values   |

#### **Example Query:**

```sql
SELECT "TABLE IDENTIFIER", "COLUMN NAME", "DATATYPE", "COLUMN_VALUE_TRANSFORMATION"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_COLUMN_DEFINITIONS
WHERE "TABLE IDENTIFIER" = 'YOUR_EXAMPLE_TABLE'
LIMIT 5;
```

---

### **3️⃣ DYNAMIC\_CORE\_LOADS**

#### **Purpose:**

Defines how data is processed in the **Core Layer**, where cleaning, validation, and transformation happen.

#### **What it Defines:**

| Column             | Description                                       |
| ------------------ | ------------------------------------------------- |
| `TABLE IDENTIFIER` | The target table name                             |
| `CORE LOAD TYPE`   | Load type for core processing (`DELTA`, `UPSERT`) |
| `ENRICHMENT FLAG`  | Indicates if additional enrichment is required    |

#### **Example Query:**

```sql
SELECT "TABLE IDENTIFIER", "CORE LOAD TYPE", "ENRICHMENT FLAG"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_CORE_LOADS
LIMIT 5;
```

---

### **4️⃣ DYNAMIC\_FTB\_INPUT\_UNIVERSE**

#### **Purpose:**

Tracks the **status of incoming files** as they move through pipeline stages.

#### **What it Defines:**

| Column           | Description                                |
| ---------------- | ------------------------------------------ |
| `FILE ID`        | Unique identifier for the file             |
| `FILE NAME`      | Actual file name in S3                     |
| `PRE VALIDATION` | Status of pre-processing validation checks |
| `CORE LOAD`      | Status of core data load                   |
| `ERROR`          | Any error messages encountered             |
| `SYSTEM DATE`    | Timestamp of the latest update             |

#### **Example Query:**

```sql
SELECT "FILE ID", "FILE NAME", "PRE VALIDATION", "CORE LOAD", "ERROR"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_FTB_INPUT_UNIVERSE
ORDER BY "SYSTEM DATE" DESC
LIMIT 5;
```

---

### **5️⃣ DYNAMIC\_ENRICHMENT\_LOADS**

#### **Purpose:**

Stores **custom SQL queries** for data enrichment tasks.

Enrichment means adding additional value to data, like:

* Looking up reference data
* Adding customer details from master tables
* Generating calculated fields

#### **What it Defines:**

| Column             | Description                          |
| ------------------ | ------------------------------------ |
| `TABLE IDENTIFIER` | The target table for enrichment      |
| `SQL_QUERY`        | The custom SQL to run for enrichment |

#### **Example Query:**

```sql
SELECT "TABLE_IDENTIFIER", "SQL_QUERY"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_ENRICHMENT_LOADS
WHERE "TABLE_IDENTIFIER" = 'YOUR_ENRICHMENT_TABLE'
LIMIT 1;
```

---

## How These Tables Work Together

| Table Name                   | Connects To                  | Relationship Example                              |
| ---------------------------- | ---------------------------- | ------------------------------------------------- |
| `DYNAMIC_DATA_LOADS`         | `DYNAMIC_FTB_INPUT_UNIVERSE` | Both share `FILE ID` for file tracking            |
| `DYNAMIC_COLUMN_DEFINITIONS` | All load processes           | Defines column structure for loading              |
| `DYNAMIC_CORE_LOADS`         | `DYNAMIC_DATA_LOADS`         | Controls next steps after raw load                |
| `DYNAMIC_ENRICHMENT_LOADS`   | `DYNAMIC_CORE_LOADS`         | Executes after core load if enrichment is flagged |

---

## Summary

By using **metadata-driven pipelines**, EVERSANA ensures:

* **Agility:** We can onboard new data sources with minimal code changes.
* **Standardization:** All data loads follow consistent, well-documented rules.
* **Transparency:** Anyone can inspect the metadata tables to understand pipeline behavior.
* **Troubleshooting Power:** You can trace any file or table through the pipeline stages.
