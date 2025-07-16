# 5. Staying Secure & Monitoring Everything 🔒👀

At EVERSANA, **security and monitoring** are built into **every step** of our data pipeline.  

We prioritize:

- **Data protection**  
- **System reliability**  
- **Proactive alerts and monitoring**  

---

## Security First 🔐

### 🔒 **AWS VPC (Virtual Private Cloud)**

Our data systems run in a **Virtual Private Cloud (VPC)**:

- An **isolated, secure network** within AWS  
- Prevents unauthorized external access  
- All services communicate inside this protected environment

---

### 🔒 **IAM (Identity and Access Management)**

**IAM controls who can access what.**

- Each team member is granted **role-based access**  
- **Least privilege principle** is followed—access is granted **only as needed**  
- All actions are logged for **audit and compliance**

---

### 🔒 **KMS (Key Management Service)**

We use **AWS KMS** to:

- **Encrypt data at rest** (stored in S3, Snowflake, etc.)  
- **Encrypt data in transit** (moving between services)  
- Manage **encryption keys securely**  

---

### 🔒 **SQL Injection Prevention**

When interacting with databases (like **Snowflake**), our developers:

- **Always use parameterized queries**  
- Avoid directly inserting user or file inputs into SQL statements  
- This prevents malicious attacks, known as **SQL Injection**

---

### 🔒 **Security Best Practices for Developers**

| Practice                              | Why It Matters                           |
|---------------------------------------|------------------------------------------|
| **Never hardcode credentials**        | Use environment variables or AWS Secrets Manager |
| **Follow least privilege principle**  | Access only the services you need       |
| **Use secure coding practices**       | Prevent security vulnerabilities        |
| **Encrypt sensitive data**            | Protect PII, PHI, and client data       |
| **Regularly review access policies**  | Ensure no excessive permissions         |

---

## Always Watching: Monitoring Everything 👀

We use **multiple monitoring tools** to ensure **pipeline health, performance, and security.**

---

### 📄 **Airflow Logs**

- View logs for every **DAG run**, **task execution**, and **failure reason**  
- Logs are accessible via the **Airflow UI**  
- Helps troubleshoot pipeline failures quickly  

---

### 📊 **AWS CloudWatch**

**AWS CloudWatch** monitors:

- **Service performance** (e.g., ECS tasks, S3 events)  
- **Resource usage** (CPU, memory, etc.)  
- **System health** (failures, bottlenecks, timeouts)

CloudWatch is our **first line of defense** for identifying cloud infrastructure issues.

*(Internal Access Link - Requires VPN)*

---

### 🧊 **Snowflake Monitoring**

Snowflake provides its own monitoring features:

- **Query profiling** to analyze slow or costly queries  
- **Warehouse utilization metrics** to optimize performance  
- **Storage and cost tracking** for budget management  

*(Internal Access Link - Requires Snowflake Login)*

---

### 🚨 **Automated Alerts**

We have **automated alerts** set up for:

- **Pipeline failures**  
- **Unexpected data volumes**  
- **Performance degradation**  
- **Security anomalies**

When something goes wrong, the relevant team members are notified **immediately**.

#### **Example Alert:**

```

Subject: ETL Pipeline Failure
Body: DAG 'sales\_data\_daily' failed during the Core Layer processing step.
Time: 03:17 AM UTC
Action Required: Check Airflow logs and resolve the issue.

```

---

## Summary

| Area                  | How We Handle It                           |
|----------------------|-------------------------------------------|
| **Network Security**  | AWS VPC, IAM, KMS                         |
| **Database Security** | Parameterized queries, encryption         |
| **Monitoring**        | Airflow Logs, CloudWatch, Snowflake tools |
| **Alerts**            | Automated notifications on failures      |

---

By combining **strong security practices** with **comprehensive monitoring**, we ensure that:

- Our **data is protected**  
- Our **pipelines run smoothly**  
- We can **respond quickly** to any issues

---
