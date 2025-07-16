# Full Glossary of Terms

This page provides a **comprehensive list of terms** used throughout the EVERSANA runbook and within our data team.

---

### ETL (Extract, Transform, Load)

Our **main data processing pipeline**:

- **Extract** data from its source.
- **Transform** it (clean, reshape, combine).
- **Load** it into its final destination (usually Snowflake).

[Learn more about ETL](https://en.wikipedia.org/wiki/Extract,_transform,_load)

---

### ELT (Extract, Load, Transform)

A variation of ETL where:

- Data is **Extracted** from the source.
- **Loaded** into the target system (like Snowflake).
- Then **Transformed** inside that system using SQL or other tools.

We use both **ETL** and **ELT** depending on the use case.

[Learn more about ELT](https://en.wikipedia.org/wiki/Extract,_load,_transform)

---

### DAG (Directed Acyclic Graph)

In **Apache Airflow**, a DAG represents:

- A **flowchart of tasks** that define a specific data process.
- Tasks run in sequence or parallel based on dependencies.
- **Acyclic** means tasks move forward without loops.

[Learn more about Airflow DAGs](https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html)

---

### AWS (Amazon Web Services)

The **cloud platform** where EVERSANA hosts:

- Data storage  
- Compute workloads  
- Cloud services for scalability and reliability

[Learn more about AWS](https://aws.amazon.com/what-is-aws/)

---

### AWS S3 (Simple Storage Service)

Amazon’s **object storage service**, used for:

- Storing raw data files  
- Keeping backups  
- Managing large-scale data securely in the cloud

[Learn more about AWS S3](https://aws.amazon.com/s3/)

---

### Apache Airflow

An **open-source workflow orchestrator**:

- Manages scheduling, monitoring, and execution of data pipelines.
- Ensures tasks run in the correct sequence with error handling.

[Visit the Apache Airflow documentation](https://airflow.apache.org/docs/)

---

### AWS ECS (Elastic Container Service)

AWS ECS is used to **run containerized applications**:

- Supports Docker containers in the cloud.
- Manages deployment and scaling automatically.

[Learn more about AWS ECS](https://aws.amazon.com/ecs/)

---

### AWS Fargate

A **serverless compute engine for containers**:

- Works with ECS to run containers without managing infrastructure.
- Automatically provisions and scales resources.

[Learn more about AWS Fargate](https://aws.amazon.com/fargate/)

---

### Docker

A **containerization platform**:

- Packages applications and dependencies into **self-contained units** called containers.
- Ensures software runs the same way in any environment.

[Visit the Docker documentation](https://docs.docker.com/)

---

### Snowflake

Our **cloud-based data warehouse**:

- Stores processed data.
- Supports advanced analytics and reporting via SQL.
- Highly scalable and supports multiple workloads.

[Visit the Snowflake documentation](https://docs.snowflake.com/)

---

### CI/CD (Continuous Integration / Continuous Deployment)

A system for **automated building, testing, and deploying** of code:

- **CI**: Automatically tests and integrates code changes.  
- **CD**: Automatically deploys code to development and production environments.

[Learn more about CI/CD](https://www.atlassian.com/continuous-delivery/ci-vs-ci-vs-cd)

---

### DQM (Data Quality Monitoring)

A process for **checking the quality of our data**:

- Validates data accuracy, completeness, and consistency.
- Prevents bad data from entering downstream systems.

[Learn more about Data Quality](https://en.wikipedia.org/wiki/Data_quality)

---

### Metadata

**"Data about data."**

In EVERSANA's systems, metadata includes:

- Column descriptions  
- File formats  
- Processing rules  
- Data lineage and audit information

[Learn more about Metadata](https://en.wikipedia.org/wiki/Metadata)

---

### Azure DevOps

A suite of tools from Microsoft for:

- Version control (Git)  
- CI/CD pipeline management  
- Project tracking and collaboration

[Visit the Azure DevOps documentation](https://learn.microsoft.com/en-us/azure/devops/)

---

### Azure Repos

The **Git-based code repository** service within Azure DevOps:

- Stores and manages our source code.  
- Supports pull requests, branching, and code reviews.

[Learn more about Azure Repos](https://learn.microsoft.com/en-us/azure/devops/repos/)

---

### Tableau

A **business intelligence (BI) tool** used for:

- Data visualization  
- Interactive dashboards  
- Reporting and analytics for business users

[Visit the Tableau documentation](https://help.tableau.com/current/guides/e-learning/en-us/)

---

### SonarCloud Analysis

A **cloud-based code quality and security analysis tool**:

- Performs static code analysis during CI/CD pipelines.  
- Identifies bugs, security vulnerabilities, and code smells.

[Visit the SonarCloud documentation](https://sonarcloud.io/documentation)

---
