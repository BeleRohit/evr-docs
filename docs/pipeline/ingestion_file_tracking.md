3.2. Ingestion & File Tracking: Getting Data In 📦
What it is: The first step of bringing data into our cloud environment.

Where it lands: All incoming raw data first lands in secure storage areas called AWS S3 buckets. Think of these as highly scalable, secure cloud folders.

Tracking: As data arrives, we automatically record its details (like file name, size, and arrival time) in special "file tracker" tables. This helps us know exactly what data has arrived and when. For example, if a sales_data_20250717.csv file arrives, its name, timestamp, and S3 path are logged.