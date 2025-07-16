Full Glossary of Terms
This page provides a comprehensive list of terms used throughout the runbook and within our data team.

ETL (Extract, Transform, Load): Our main process! It means we Extract data from its source, Transform it (clean, reshape, combine), and then Load it into its final destination.

Learn more about ETL

ELT (Extract, Load, Transform): A variation where data is loaded into the target system first, then transformed within that system. We use both ETL and ELT concepts.

Learn more about ELT

DAG (Directed Acyclic Graph): In our Airflow system, this is like a flowchart that defines a series of tasks and the order they need to run in for a specific data process.

Learn more about Airflow DAGs

AWS (Amazon Web Services): The "cloud" where we host most of our data systems and services.

Learn more about AWS

AWS S3 (Simple Storage Service): Amazon's cloud storage. Imagine it as super-scalable, secure folders in the sky where we store our data files.

Learn more about AWS S3

Apache Airflow: An open-source tool that acts as our "orchestrator" or "scheduler." It makes sure all our data processes run on time and in the correct order.

Visit the Apache Airflow documentation

AWS ECS (Elastic Container Service): An AWS service that helps us run our data processing applications in isolated "containers."

Learn more about AWS ECS

AWS Fargate: A "serverless" technology that works with ECS. It means we don't have to worry about managing the actual servers that run our applications; AWS handles it for us.

Learn more about AWS Fargate

Docker: A technology that packages our applications (and all their necessary parts) into self-contained units called "containers." This ensures our code runs exactly the same everywhere.

Visit the Docker documentation

Snowflake: Our powerful cloud-based data warehouse. This is where most of our processed data lives and where our analytical tools connect.

Visit the Snowflake documentation

CI/CD (Continuous Integration / Continuous Deployment): Our automated way of building, testing, and releasing new code changes quickly and reliably.

Learn more about CI/CD

DQM (Data Quality Monitoring): Our system for checking and ensuring that our data is accurate, complete, and consistent.

Learn more about Data Quality

Metadata: "Data about data." In our world, this means information stored in special tables that describes our files, columns, and the rules for processing them.

Learn more about Metadata

Azure DevOps: A suite of development tools from Microsoft that we use for version control, CI/CD pipelines, and project management.

Visit the Azure DevOps documentation

Azure Repos: The Git-based code hosting service within Azure DevOps.

Learn more about Azure Repos

Tableau: A popular business intelligence tool used for data visualization and reporting.

Visit the Tableau documentation

Sonar Cloud Analysis: A cloud-based service for continuous code quality and security analysis.

Visit SonarCloud documentation