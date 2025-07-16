4. How We Build & Deploy Code: Our CI/CD Process 🚀
Our CI/CD { data-tooltip="Continuous Integration / Continuous Deployment: Our automated way of building, testing, and releasing new code changes quickly and reliably." } process is our automated pipeline for getting new code (for our data processes) from a developer's computer into our live systems. We use Azure DevOps { data-tooltip="A suite of development tools from Microsoft that we use for version control, CI/CD pipelines, and project management." } for this.

Here's a simplified breakdown:

You Write Code: As a developer, you'll write new code for our data processes (e.g., a new Apache Airflow DAG { data-tooltip="Directed Acyclic Graph: In our Airflow system, this is like a flowchart that defines a series of tasks and the order they need to run in for a specific data process." }, or a change to a data transformation script). You do this in a "feature branch" of our code repository (Azure Repos).

Propose Changes (Pull Request - PR): When your code is ready, you create a "Pull Request" (PR). This is a request to merge your changes into the main codebase.

Learn how to create a Pull Request in Azure DevOps

Automated Checks (CI): Creating a PR automatically triggers our Continuous Integration (CI) pipeline. This pipeline:

Checks Code Quality: It automatically scans your code for errors and best practices using tools like Sonar Cloud Analysis.

Builds Components: It builds any necessary components, like new Docker images { data-tooltip="A technology that packages our applications (and all their necessary parts) into self-contained units called 'containers.' This ensures our code runs exactly the same everywhere." }.

Important: Your PR can only be merged if these automated checks pass, and if other team members review and approve your code. Code reviews are crucial for maintaining quality!

Merge to 'dev': Once approved, your changes are merged into our 'dev' (development) branch.

Deploy to Development (CD): Merging to 'dev' automatically kicks off our Continuous Deployment (CD) pipeline for the development environment. This means your new code is automatically deployed to our development data pipeline, where we can test it thoroughly.

Deploy to Production: After successful testing in the development environment and final approvals, your changes are merged into the 'main' (production) branch. This triggers another CD pipeline, deploying your changes to our live production environment.

Potential Improvements for this Section:
Actual CI/CD Diagram: Replace the placeholder (Imagine a simplified CI/CD flow diagram here) with the actual diagram from the original runbook.

Screenshots: Include small screenshots of key steps in Azure DevOps (e.g., how to create a PR, what a passing pipeline looks like).

"Why CI/CD?" Explanation: Briefly explain the benefits of CI/CD (e.g., faster deployments, fewer errors, more reliable code) for a new hire.

Code Review Best Practices: Briefly mention the importance of code reviews as part of the PR process.