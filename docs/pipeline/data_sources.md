# 3.1. Data Sources: Where Data Begins 📥

## What Are Data Sources?

**Data Sources** are the **starting point** of our entire data pipeline.  
This is where **all raw information originates** before being processed.

Without data sources, there is **no data pipeline**—this is **Step 1** in turning raw data into actionable insights.

---

## Examples of Data Sources

We collect data from **multiple systems** and **external partners**.  
Here are common examples:

| Source Type                       | Description & Example                               |
|----------------------------------|----------------------------------------------------|
| **CRM Systems**                  | Daily sales figures, customer records              |
| **External Partners**            | Third-party data feeds, vendor files               |
| **APIs (Application Interfaces)**| Real-time data like survey responses or webhooks   |
| **Operational Databases**        | Internal transactional systems (e.g., orders, billing) |
| **Marketing Platforms**          | Campaign performance data, clickstream events      |
| **Public Data**                  | External datasets like market trends or weather    |

---

## How It Works

### **File Types & Formats**

The raw data can arrive in **various formats**, including:

- **CSV** – Comma-Separated Values (most common for flat files)  
- **Parquet** – Optimized columnar storage for large datasets  
- **JSON** – Used for nested or API-based data  
- **XML** – Sometimes used by legacy systems  
- **SQL Dumps** – For large database extracts  

---

### **Delivery Methods**

| Method                | Description                                  |
|----------------------|----------------------------------------------|
| **S3**                  | Files are uploaded directly on S3 
|**SFTP / FTP Servers** | Files securely transferred to AWS S3        |
| **API Calls**          | Data pushed to our systems via APIs         |
| **Manual Uploads**     | Occasionally, data is uploaded manually     |
| **Streaming Events**   | Real-time data streams (Kafka, Webhooks)    |

---

## Data Landing Zone

All incoming data is first placed in our **AWS S3 Landing Zone**:

- A secure **"raw data" storage location**  
- No transformations or changes are applied here  
- Serves as a **data backup** and **audit point**

---

## Why This Matters

Understanding where the data comes from is critical because:

- It affects **data quality**  
- Determines **how the data should be processed**  
- Helps in **troubleshooting issues** when raw data is missing or incorrect

---

## Summary

- **Data Sources** are the **entry point** for the pipeline  
- Data arrives in **various formats and from various systems**  
- Everything starts by **landing raw data in AWS S3**

---

