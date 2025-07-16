# 4. How We Build & Deploy Code: Our CI/CD Process 🚀

Our **CI/CD (Continuous Integration / Continuous Deployment)** process is the **automated pipeline** we use to move new code from a developer’s laptop into our live data systems safely and efficiently.

![CI/CD Pipeline Diagram](../assets/ci_cd_diagram.pn)

We use **Azure DevOps** for:

- Version control (code repositories via Azure Repos)  
- CI/CD pipelines (automated testing and deployment)  
- Code review and project management

---

## Overview of the CI/CD Pipeline

### 1️⃣ **You Write Code**

As a developer, you'll:

- Write new code for our data processes, such as:  
  - **Apache Airflow DAGs** (for scheduling data workflows)  
  - **Data transformation scripts** (ETL/ELT code)  
- Work inside a **feature branch** of our code repository (Azure Repos).

This ensures your changes are isolated and easy to review.

---

### 2️⃣ **Propose Changes (Create a Pull Request - PR)**

Once your feature is ready:

- You create a **Pull Request (PR)** in Azure DevOps.  
- A PR is a formal request to merge your feature branch into the **`dev` branch**.

This step kicks off the **review and testing process**.

[Learn how to create a Pull Request in Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/repos/git/pull-requests)

---

### 3️⃣ **Automated Checks (Continuous Integration - CI)**

When you create a PR, our **CI pipeline** automatically runs:

#### 🔍 **Code Quality Checks**

- We use **SonarCloud Analysis** to:
  - Scan for bugs  
  - Identify security issues  
  - Detect code smells (bad practices)

---

#### 🛠️ **Build Components**

- The pipeline builds necessary components, such as:
  - **Docker images** for containerized data jobs  
  - **Packaging Airflow DAGs** or Python scripts for deployment  

---

#### ✅ **Pass Requirements**

Your PR can only be merged when:

- All automated checks **pass**  
- At least one team member **reviews and approves your code**

Code reviews are essential for:

- Catching bugs early  
- Sharing knowledge  
- Maintaining code quality and consistency

---

### 4️⃣ **Merge to `dev`**

Once approved, your changes are merged into the **`dev` branch**.

This is our **development environment** where new code is first tested end-to-end.

---

### 5️⃣ **Deploy to Development (Continuous Deployment - CD)**

Merging into `dev` triggers the **CD pipeline**:

- Your code is **automatically deployed** to our **development data pipelines**.  
- This lets the team **test new workflows in a safe environment** before going live.

---

### 6️⃣ **Deploy to Production**

After successful testing in development:

- Your team creates a **PR from `dev` to `main`** (the production branch).
- Once approved, the **production CD pipeline** deploys your code to **live systems**.

---


## Why CI/CD?

**CI/CD is crucial for modern data engineering because it:**

- **Speeds up deployment** – Faster delivery of new features and bug fixes.  
- **Reduces human error** – Automated pipelines catch issues early.  
- **Ensures consistency** – Same process for every deployment.  
- **Improves collaboration** – Code reviews promote shared knowledge and quality control.

---

## Code Review Best Practices

When reviewing or submitting a PR:

- Write **clear, descriptive PR titles and messages**.
- Keep PRs **small and focused** (one change per PR if possible).  
- Use **comments** to explain non-obvious code decisions.  
- **Be constructive** in feedback—focus on improvement, not criticism.  
- Review **logic, security, and performance**, not just syntax.

---

## Tools Involved

| Tool               | Purpose                                      |
|-------------------|----------------------------------------------|
| **Azure DevOps**   | Version control, PRs, pipelines              |
| **Azure Repos**    | Git-based code repository                    |
| **SonarCloud**     | Code quality and security checks             |
| **Docker**         | Packaging and running code in containers     |
| **Airflow**        | Scheduling and orchestrating data workflows  |

---

# End of CI/CD Section


