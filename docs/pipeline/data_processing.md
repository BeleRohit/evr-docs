3.3. Orchestration: The Master Scheduler ⏰
What it is: This stage is like our control tower, making sure all data processing steps run on time and in the correct sequence.

Our Tool: We use Apache Airflow for this. Airflow provides a web-based UI where you can monitor DAGs.

Access the Airflow UI (Internal Link - Requires VPN/Access)

How it works: Airflow uses DAGs (those flowcharts we talked about!) to define our workflows. It can start a process when a new file is detected in S3 (via a "file sensor"), or it can run on a pre-defined schedule (e.g., every morning at 3 AM). For example, a DAG named daily_sales_pipeline might be configured to run once a new sales_data file lands in S3.