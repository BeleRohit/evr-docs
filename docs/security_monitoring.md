5. Staying Secure & Monitoring Everything 🔒👀
Security and monitoring are built into every single step of our data pipeline.

Security First:
AWS VPC { data-tooltip="Virtual Private Cloud: Our data systems live in a secure, isolated network within AWS." } (Virtual Private Cloud): Our data systems live in a secure, isolated network within AWS.

IAM { data-tooltip="Identity and Access Management: This controls who can access our AWS resources and what actions they are allowed to perform. Access is granted based on your role and what you need to do." } (Identity and Access Management): This controls who can access our AWS resources and what actions they are allowed to perform. Access is granted based on your role and what you need to do.

KMS { data-tooltip="Key Management Service: We use this to encrypt our sensitive data, both when it's stored and when it's moving between systems." } (Key Management Service): We use this to encrypt our sensitive data, both when it's stored and when it's moving between systems.

SQL Injection Prevention: When our code talks to databases (like Snowflake), we always use a secure method called "parameterized queries." This is a technical detail, but it's crucial for preventing malicious attacks.

Always Watching (Monitoring):
Airflow Logs: We check Apache Airflow logs to see if our data workflows are running smoothly or if there are any errors.

AWS CloudWatch: This is our main tool for monitoring the performance and health of all our AWS services (like AWS S3, AWS ECS tasks, etc.).

Access AWS CloudWatch (Internal Link - Requires VPN/Access)

Snowflake Monitoring: Snowflake has its own built-in tools that help us track how well our queries are performing and manage costs.

Access Snowflake Monitoring (Internal Link - Requires Login)

Alerts: We have automated alerts set up. If something goes wrong (like a pipeline failure, unexpected data volume, or performance issues), the right people are notified immediately.

Potential Improvements for this Section:
Accessing Monitoring Tools: Provide direct links or instructions on how a new user can access Airflow logs, AWS CloudWatch dashboards, and Snowflake monitoring interfaces.

Example Alert: Show a very simple example of what an alert might look like (e.g., "Email: ETL Pipeline Failure - DAG 'sales_data_daily' failed in Core Layer").

Security Best Practices for Developers: Briefly list common security practices relevant to developers (e.g., "Never hardcode credentials," "Follow least privilege principle").