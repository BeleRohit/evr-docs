# 3.2. Ingestion & File Tracking: Getting Data In 📦

## What Is Ingestion?

**Ingestion** is the **first technical step** in our data pipeline after data is generated or sent by a source.  
It refers to the process of **bringing raw data into our cloud environment** so that it can be processed.

---

## Where Does the Data Land?

All incoming raw data is stored in **AWS S3 Buckets**.

### **What is AWS S3?**

- Think of S3 as **highly scalable, secure cloud folders**  
- It's a **durable, cost-effective, and secure storage system**  
- We use it as our **"Landing Zone"** for raw data

---

## Example: File Arrival in S3

Let’s say the following file arrives:

```

sales\_data\_20250717.csv

```

When it lands in S3:

- The file is stored under a specific path like:

```

s3://eversana-raw-data/sales/2025/07/17/sales\_data\_20250717.csv

````

---

## How Do We Track Incoming Files?

We use **automated file tracking** to record important information as files arrive.

### **What We Track:**

| Tracked Detail   | Description                          |
|-----------------|--------------------------------------|
| **File Name**   | Name of the incoming file             |
| **S3 Path**     | Exact cloud storage location          |
| **File Size**   | Size of the file in bytes             |
| **Arrival Time**| When the file landed in the S3 bucket |
| **Source System**| Where the file originated from       |

---

## Why Do We Track Files?

File tracking is critical because it:

- Provides **end-to-end data observability**  
- Helps us **verify data completeness** (did we receive all expected files?)  
- Allows us to **troubleshoot issues** (e.g., missing files, duplicates, delayed arrivals)  
- Supports **auditing and compliance** requirements

---

## Where Is This Information Stored?

We store file tracking details in **special metadata tables** in **Snowflake**, such as:

### **DYNAMIC_FTB_INPUT_UNIVERSE Table**

| Column Name         | What It Stores                      |
|--------------------|-------------------------------------|
| **FILE ID**         | Unique identifier for the file      |
| **FILE NAME**       | The actual file name (e.g., `sales_data_20250717.csv`) |
| **S3 FILE PATH**    | Where the file is stored in S3      |
| **ARRIVAL TIMESTAMP**| Exact time the file arrived        |
| **PRE VALIDATION STATUS**| Whether the file passed initial checks |

---

## Example SQL Query (Snowflake):

```sql
SELECT "FILE ID", "FILE NAME", "S3 FILE PATH", "ARRIVAL TIMESTAMP"
FROM EVERSANA_UTILITY_DB.MONITORING.DYNAMIC_FTB_INPUT_UNIVERSE
WHERE "FILE NAME" LIKE 'sales_data%'
ORDER BY "ARRIVAL TIMESTAMP" DESC
LIMIT 5;
````

---

## Summary

| Step                     | What Happens                           |
| ------------------------ | -------------------------------------- |
| **Data Arrival**         | Raw files land in **AWS S3 buckets**   |
| **File Tracking Begins** | File details are logged into Snowflake |
| **Audit Trail**          | We maintain a full history of arrivals |
| **Next Step**            | Pipeline reads the file for processing |

---

By **tracking every file** that enters our system, we ensure **pipeline reliability**, **data integrity**, and **full visibility** into the data ingestion process.