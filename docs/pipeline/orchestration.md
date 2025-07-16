# 3.3. Orchestration: The Master Scheduler ⏰

## What is Orchestration?

**Orchestration** is like the **control tower** of our data pipeline.

It ensures:

- **Data processing steps** run **on time**
- Tasks happen in the **correct order**
- Systems know **when to wait** and **when to move forward**

Without orchestration, we'd have to **manually kick off tasks** or rely on basic cron jobs, which can be fragile and error-prone.  
Orchestration brings **automation, reliability, and visibility** to the process.

---

## Our Orchestration Tool: **Apache Airflow**

At EVERSANA, we use **Apache Airflow** to manage and schedule all data pipeline workflows.

### **Why Airflow?**

| Feature                 | What It Means                           |
|------------------------|----------------------------------------|
| **DAGs**                | Define workflows as Directed Acyclic Graphs |
| **Scheduling**          | Run tasks on **predefined intervals** (e.g., daily at 3 AM) |
| **Event-based Triggers**| Start tasks when **new files arrive** (e.g., via S3 File Sensor) |
| **Retries & Alerts**    | Automatically handle failures and notify the team |
| **Visibility**          | Web UI to monitor task status and logs |

---

## Accessing Airflow

Airflow provides a **web-based interface (UI)** where you can:

- **Monitor DAGs**  
- Check **logs of each task**  
- **Pause / Resume workflows**  
- **Rerun failed tasks**

📂 **Access Airflow UI**  
*(Internal Link – Requires VPN / Internal Access Rights)*

---

## How Does It Work?

### **What is a DAG?**

A **DAG (Directed Acyclic Graph)** represents:

- A **workflow** or **pipeline**  
- Defined by **tasks (nodes)** connected by **dependencies (edges)**  
- **No loops** – data flows in one direction only

---

### **Trigger Mechanisms:**

| Trigger Type        | Example Scenario                                   |
|--------------------|----------------------------------------------------|
| **File Sensor**     | Detect when a new file lands in **S3**            |
| **Scheduled Runs**  | Run daily at a set time, e.g., **3:00 AM daily**  |
| **Manual Triggers** | Run manually from Airflow UI for testing/debugging |

---

## Real Example: `daily_sales_pipeline`

**Workflow:**

1. **File Sensor:** Waits for `sales_data` file in S3  
2. **Extraction:** Pulls raw data from S3  
3. **Transformation:** Cleans and processes the data  
4. **Load:** Inserts the processed data into Snowflake  
5. **Data Quality Checks:** Validates the load was successful  
6. **Notification:** Sends a success/failure alert to the team

---

## Why Use Orchestration?

| Benefit                | Why It Matters                             |
|-----------------------|-------------------------------------------|
| **Automation**         | No manual effort for pipeline runs        |
| **Reliability**        | Handles retries and error notifications   |
| **Visibility**         | Full monitoring via Airflow UI            |
| **Scalability**        | Easily add new workflows or adjust schedules |
| **Consistency**        | Ensures data processes follow the same logic every time |

---

## Summary

- **Apache Airflow** is our **Master Scheduler**  
- It controls **when** and **how** our pipelines run  
- Provides **automation**, **visibility**, and **error handling**  
- Uses **DAGs** to define and manage workflows
