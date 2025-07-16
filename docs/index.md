EVERSANA ETL Process Runbook: Your Guide to Data at EVERSANA
Version: 1.0
Date: July 17, 2025
Purpose: Welcome to the team! This document is your friendly introduction to how we handle data at EVERSANA. It will guide you through our core data pipeline, explaining how data moves from its source, gets processed, and becomes ready for use. No prior knowledge is needed – we'll explain everything step-by-step!

1. Welcome to the Team! 👋
We're excited to have you on board! Data is at the heart of what we do at EVERSANA. This runbook will help you understand our data "factory" – how we bring in raw information, clean and organize it, and make it valuable for our business insights. Think of it as a map to our data landscape.

Potential Improvements for this Section:
Onboarding Checklist: Add a link to a general onboarding checklist for new hires, which could include initial setup steps for tools and systems.

Team Directory: Include a link to a team directory or organizational chart to help new members understand who does what and who to reach out to.

2. Quick Glossary: Understanding Our Lingo 📖
Here are some common terms you'll encounter. Don't worry about memorizing them all at once; this section is here for quick reference! You can also find a full glossary here.

ETL { data-tooltip="Extract, Transform, Load: Our main process! We Extract data from its source, Transform it (clean, reshape, combine), and then Load it into its final destination." }

ELT { data-tooltip="Extract, Load, Transform: A variation where data is loaded into the target system first, then transformed within that system. We use both ETL and ELT concepts." }

DAG { data-tooltip="Directed Acyclic Graph: In our Airflow system, this is like a flowchart that defines a series of tasks and the order they need to run in for a specific data process." }

AWS { data-tooltip="Amazon Web Services: The 'cloud' where we host most of our data systems and services." }

AWS S3 { data-tooltip="Simple Storage Service: Amazon's cloud storage. Imagine it as super-scalable, secure folders in the sky where we store our data files." }

Apache Airflow { data-tooltip="An open-source tool that acts as our 'orchestrator' or 'scheduler.' It makes sure all our data processes run on time and in the correct order." }

AWS ECS { data-tooltip="Elastic Container Service: An AWS service that helps us run our data processing applications in isolated 'containers.'" }

AWS Fargate { data-tooltip="A 'serverless' technology that works with ECS. It means we don't have to worry about managing the actual servers that run our applications; AWS handles it for us." }

Docker { data-tooltip="A technology that packages our applications (and all their necessary parts) into self-contained units called 'containers.' This ensures our code runs exactly the same everywhere." }

Snowflake { data-tooltip="Our powerful cloud-based data warehouse. This is where most of our processed data lives and where our analytical tools connect." }

CI/CD { data-tooltip="Continuous Integration / Continuous Deployment: Our automated way of building, testing, and releasing new code changes quickly and reliably." }

DQM { data-tooltip="Data Quality Monitoring: Our system for checking and ensuring that our data is accurate, complete, and consistent." }

Metadata { data-tooltip="Data about data: Information stored in special tables that describes our files, columns, and the rules for processing them." }

Potential Improvements for this Section:
Interactive Glossary (Web Version): The data-tooltip attribute is used here for hover-over effects (requires Material for MkDocs theme and attr_list extension).

Visual Aids: For complex terms, consider adding small icons or simple diagrams next to the definition.

Pronunciation Guide: For acronyms or technical terms that might be hard to pronounce, a phonetic guide could be helpful.