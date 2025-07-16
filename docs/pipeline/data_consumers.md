# 3.5. Data Consumers: Using the Data 📈

Once data has been **processed and validated**, it becomes **available to the end-users**—our **Data Consumers**.

---

## Who Uses the Data?

**This is where you come in!**  
Our processed data is consumed by various teams and tools across EVERSANA.

### **Examples of Data Consumers:**

| Role/Team              | How They Use the Data                          |
|-----------------------|-----------------------------------------------|
| **Data Analysts**      | Build reports and dashboards using Tableau   |
| **Data Scientists**    | Train machine learning models, run analyses  |
| **Business Users**     | View reports, track KPIs, make data-driven decisions |
| **Downstream Applications** | Connect to Presentation Layer for real-time data |

---

## Real Example: Monthly Sales Dashboard

- Our **Monthly Sales Dashboard** in **Tableau** pulls data directly from the **Presentation Layer** in **Snowflake**.  
- This ensures the dashboard reflects **up-to-date, cleansed, and validated data**.

---

## How Do Consumers Access the Data?

### **Primary Access Method:**  
Most users access data via **Snowflake Presentation Layer tables**.

These tables contain:

- **Finalized, business-ready data**  
- Pre-aggregated or pre-joined views for specific use cases  
- Data that's ready for direct consumption with **minimal additional processing**

---

## Access Tools

| Tool          | Purpose                             |
|---------------|-------------------------------------|
| **Snowflake** | SQL-based data exploration          |
| **Tableau**   | Visual reporting and dashboards     |
| **Jupyter/IDE** | Data science and ad hoc analysis   |
| **APIs / Applications** | Real-time or batch data consumption |

---

## Summary

- **Presentation Layer = Consumer Layer**  
- It provides **clean, structured, and ready-to-use data**  
- Consumers **do not need to know the raw data structure**—the pipeline handles the complexity

