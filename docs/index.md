# EVERSANA ETL Process Runbook: Your Guide to Data at EVERSANA

**Version:** 1.0  
**Date:** July 17, 2025  

---

## Purpose

**Welcome to the team!** 👋

We're excited to have you on board!  
At EVERSANA, **data is at the heart of what we do**. Whether it’s improving healthcare outcomes, analyzing market trends, or helping our clients make smarter decisions—our data systems power the insights behind it all.

This runbook is designed to give you a **clear, step-by-step introduction to our data pipeline**, even if you're completely new to these systems.  
Think of it as a **map to our data landscape**—you'll learn how raw information comes in, how it’s cleaned and organized, and how it becomes ready for analysis and business use.

---

## 1. Welcome to the Team! 👋

At EVERSANA, we think of data operations like a **factory assembly line**:

- We **bring in raw data** from multiple sources (clients, partners, internal systems).
- We **clean, standardize, and transform** that data to make it useful.
- We **store it in secure, scalable systems** where our analysts and applications can easily access it.

This document will guide you through each part of that process so you can hit the ground running.

---

## 2. Quick Glossary: Understanding Our Lingo 📖

Here are some key terms you'll encounter in your work. Don’t worry about memorizing them all—this section is here for quick reference whenever you need it!

### ETL

**Extract, Transform, Load**

This is our **core data pipeline process**:

- **Extract**: We pull data from various sources. This could be client systems, APIs, files in storage, or databases.
- **Transform**: We clean the data, reshape it into the correct formats, remove duplicates, handle missing values, and sometimes combine it with other data sources.
- **Load**: We store the transformed data into our central data warehouse (Snowflake) so it’s ready for reporting, analytics, or downstream systems.

ETL is like cooking: you gather ingredients (extract), prepare and cook them (transform), and serve the final dish (load).

---

### ELT

**Extract, Load, Transform**

This is a **variation of ETL** where:

- We **Extract** data from the source.
- We **Load** the raw data directly into Snowflake (our data warehouse).
- We then **Transform** the data **inside Snowflake** using SQL.

This approach is useful when you want to retain raw data for auditing or historical reference while transforming only the parts you need later.

---

### DAG

**Directed Acyclic Graph**

In **Apache Airflow**, a DAG is like a **flowchart** that defines the sequence of tasks in a pipeline.

- Each **task** represents a step in a data process (like extracting data, running a validation, or moving files).
- The **"Directed"** part means the tasks have a specific order.
- The **"Acyclic"** part means there are **no loops**—tasks don’t go in circles.

Think of a DAG as the **blueprint** that Airflow follows to automate our ETL processes.

---

### AWS

**Amazon Web Services**

AWS is our **cloud computing platform**. We use it to host almost all of our data systems.  
It provides computing power, storage, databases, networking, and security services—all accessible over the internet.

---

### AWS S3

**Simple Storage Service**

S3 is Amazon’s **cloud storage service**.  
Imagine it as having access to **infinite folders in the cloud** where we can store any kind of file—raw data, logs, reports, and backups.

- It’s **scalable**: handles petabytes of data.
- It’s **secure**: with encryption, access controls, and auditing.
- We often use S3 as the first landing zone for incoming client files.

---

### Apache Airflow

**Workflow Orchestration Tool**

Airflow is our **scheduler and orchestrator** for data pipelines.

- It decides **what task runs when**, in what order, and under what conditions.
- Airflow handles retries if something fails, sends alerts, and keeps track of execution logs.

Think of it as the **conductor of the data orchestra**, making sure each system plays its part at the right time.

---

### AWS ECS

**Elastic Container Service**

ECS lets us run **Docker containers** (packaged applications) in the cloud.

- It provides **container orchestration**—deciding where and how containers run.
- It manages resource scaling so we can handle large workloads without worrying about underlying servers.

We use ECS to run parts of our ETL pipelines, custom APIs, and processing jobs.

---

### AWS Fargate

**Serverless Containers**

AWS Fargate is a special mode of running containers in ECS **without managing servers**.

- We tell Fargate how much CPU and memory we need.
- AWS handles all the **infrastructure behind the scenes**.

This allows us to focus only on building data applications, not on server setup or maintenance.

---

### Docker

**Containerization Technology**

Docker allows us to package applications into **self-contained units called containers**.  

- Each container includes the application code, dependencies, libraries, and configurations.
- This ensures the code **runs the same way everywhere**—whether on your laptop, in AWS, or in ECS.

Docker simplifies deployment, testing, and scaling.

---

### Snowflake

**Cloud Data Warehouse**

Snowflake is where we **store, process, and query most of our data**.

- It’s **highly scalable** and handles large datasets easily.
- We use it for **analytics, reporting, dashboards, and data sharing**.

Snowflake supports **SQL-based querying**, making it accessible to both technical and non-technical users.

---

### CI/CD

**Continuous Integration / Continuous Deployment**

This is our **automated pipeline for code changes**:

- **Continuous Integration (CI)**: We automatically build and test code whenever changes are made. This helps catch bugs early.
- **Continuous Deployment (CD)**: After testing, the code is automatically deployed to production or staging environments without manual steps.

CI/CD allows us to **release updates quickly and reliably**, improving both speed and quality.

---

### DQM

**Data Quality Monitoring**

DQM ensures our data is:

- **Accurate**: Correct and reliable.
- **Complete**: No missing critical information.
- **Consistent**: Matches expected formats and rules.

We have systems in place to **validate data at every step**, from ingestion to storage.

---

### Metadata

**Data About Data**

Metadata describes:

- **What the data is** (e.g., file names, column descriptions).
- **Where it came from** (source systems, extraction dates).
- **How it should be processed** (transformation rules, data types).

We store metadata in special tables, making it easier to **automate ETL jobs and maintain data lineage**.

---

## End of Document

Welcome again! If you ever get stuck or have questions, don’t hesitate to reach out to the team. We’re here to help you succeed.

