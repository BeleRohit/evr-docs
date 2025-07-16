
# EVERSANA Code Deployment Guide: How to Deploy Your Code 🚀

**Version:** 1.0  
**Date:** July 17, 2025  

---

## Purpose

Welcome to the **EVERSANA developer workflow!**

As a developer, you’ll regularly need to **deploy your code changes** into our systems.  
This document provides a **complete, step-by-step guide** to help you understand how code deployment works at EVERSANA, even if you're new to Git or Azure DevOps.

By the end of this guide, you’ll know how to:

- Work with Git branches  
- Push your code to Azure Repos  
- Create Pull Requests (PRs)  
- Deploy to development and production environments  
- Verify your deployment

---

## Deployment Workflow Overview

We use a **branch-based development workflow** combined with **CI/CD pipelines** for safe and efficient code deployment.

### Branching Model:

| Branch        | Purpose                                     |
|---------------|---------------------------------------------|
| `dev`         | Active development and testing environment  |
| `main`        | Production-ready, stable code               |
| `feature/*`   | New features or bug fixes (temporary branch)|

---

## Step 1: Clone the Repository

Start by **cloning the code repository** from Azure Repos to your local machine.

### Command:

```bash
git clone <repository-url>
````

Replace `<repository-url>` with the link shared by your team.

This will download the repository to your machine.

---

## Step 2: Update Your Local `dev` Branch

Make sure your local `dev` branch is **up-to-date** before starting any new work.

### Commands:

```bash
git checkout dev          # Switch to the dev branch
git pull origin dev       # Update local dev with the latest changes
```

This ensures you are working on the latest codebase.

---

## Step 3: Create a New Feature Branch

All new work should be done in a **separate feature branch** to keep changes isolated and reviewable.

### Command:

```bash
git checkout -b your-descriptive-branch-name
```

### Naming Convention Example:

| Type    | Example                 |
| ------- | ----------------------- |
| Feature | `feature/add-new-dag`   |
| Bugfix  | `bugfix/fix-s3-path`    |
| Hotfix  | `hotfix/urgent-dag-fix` |

---

## Step 4: Make Your Changes

Edit the relevant files depending on your task.

Examples:

* **Apache Airflow DAGs** – Define or update task workflows.
* **Python scripts** – Implement transformations or business logic.
* **SQL scripts** – Modify data queries or models.
* **Configuration files** – Update environment settings or parameters.

---

## Step 5: Stage and Commit Your Changes

Once your changes are ready:

### Stage the changes:

```bash
git add .
```

### Commit the changes with a clear message:

```bash
git commit -m "Short, clear description of your changes"
```

---

### Useful Git Commands

| Action                | Command                        |
| --------------------- | ------------------------------ |
| Stage all changes     | `git add .`                    |
| Commit changes        | `git commit -m "Your message"` |
| Check status          | `git status`                   |
| View unstaged changes | `git diff`                     |
| View commit history   | `git log`                      |

---

## Step 6: Push Your Feature Branch

Push your new branch to Azure Repos so that others can review your code.

### Command:

```bash
git push -u origin your-descriptive-branch-name
```

The `-u` flag links your local branch to the remote branch for easier future pushes.

---

## Step 7: Create a Pull Request (PR) to `dev`

In **Azure DevOps**, create a **Pull Request (PR)**:

1. Navigate to your repository in Azure DevOps.
2. Open a PR from **your feature branch into `dev`**.
3. Provide a **clear title and description** of what your PR does.
4. Assign reviewers (your team will guide you on reviewers).
5. Azure Pipelines will run automated checks (tests, linting, etc.).

---

## Step 8: Merge into `dev`

Once your PR is:

* **Approved by reviewers**
* **All checks pass**

You can merge your changes into the `dev` branch.

### What happens next?

* Your code is **automatically deployed to the development environment** via CI/CD pipelines.
* This allows your team to test the changes in a safe environment.

---

## Step 9: Create a Pull Request (PR) to `main`

After successful testing in the development environment:

1. Create a **new PR from `dev` to `main`**.
2. This PR is reviewed again to ensure production readiness.
3. Automated checks will run as part of the pipeline.

---

## Step 10: Merge into `main` (Production Deployment)

When the `main` PR is:

* **Approved by reviewers**
* **All checks pass**

Merging the PR will **automatically deploy your changes to production**.

Our **CI/CD pipeline handles the deployment process**—no manual server steps are needed.

---

## Step 11: Verify Your Deployment

After production deployment:

1. **Check the Airflow UI** to confirm:

   * New DAGs appear (if applicable).
   * DAGs are scheduled and running properly.

2. **Monitor Logs** for any errors or unexpected behavior.

3. **Test Data Pipelines** if your changes affect ETL jobs.

---

## Troubleshooting Tips

### Common Deployment Issues:

| Issue                              | Where to Check                         |
| ---------------------------------- | -------------------------------------- |
| Pipeline failure                   | Azure DevOps Pipeline logs             |
| Merge conflicts                    | Local Git terminal                     |
| DAG not visible in Airflow         | Airflow UI logs & DAG folder structure |
| Failing automated tests            | Azure Pipeline test output             |
| Environment variable/config errors | Pipeline configs & deployment logs     |

---

## Quick Git Command Reference

| Action                | Command                             |
| --------------------- | ----------------------------------- |
| Clone repository      | `git clone <repository-url>`        |
| Switch to a branch    | `git checkout <branch-name>`        |
| Create new branch     | `git checkout -b <new-branch-name>` |
| Pull latest changes   | `git pull origin <branch-name>`     |
| Stage all changes     | `git add .`                         |
| Commit changes        | `git commit -m "Your message"`      |
| Check status          | `git status`                        |
| View unstaged changes | `git diff`                          |
| View commit history   | `git log`                           |
| Push new branch       | `git push -u origin <branch-name>`  |

---

## Summary: Deployment Flow

```
Local Feature Branch  
        │
        └──> Pull Request to `dev`  
                │
                └──> Automated Tests & Review  
                        │
                        └──> Merge to `dev`  
                                │
                                └──> Deploy to Development  
                                        │
                                        └──> Pull Request to `main`  
                                                │
                                                └──> Review & Approval  
                                                        │
                                                        └──> Merge to `main`  
                                                                │
                                                                └──> Deploy to Production
```

---

## Final Notes

* **Always verify your deployments** in Airflow and monitor logs post-deployment.
* Use **clear commit messages** and **descriptive branch names** to make the process collaborative and easy to review.
* If you encounter issues, ask your team leads or check Azure DevOps logs for details.

---


