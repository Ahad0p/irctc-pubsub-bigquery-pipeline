IRCTC Real-Time Data Streaming Pipeline (GCP)
📌 Project Overview

This project demonstrates an end-to-end real-time data engineering pipeline built on Google Cloud Platform (GCP).
Mock IRCTC-style user data is generated using Python, published to Pub/Sub, processed using Dataflow (Apache Beam), and finally streamed into BigQuery for analytics.

All resources were created, tested, and cleanly deleted after execution to ensure cost and security best practices.

🏗️ Architecture

Python Publisher
↓
Google Cloud Pub/Sub
↓
Google Cloud Dataflow (Streaming)
↓
Google BigQuery

🧰 Tech Stack

Python

Google Cloud Pub/Sub

Google Cloud Dataflow (Apache Beam)

Google BigQuery

Google Cloud Storage (staging & temp)

⚙️ Data Pipeline Description

1.Python script generates mock IRCTC user data in JSON format

2.Messages are published to a Pub/Sub topic

3.Dataflow streaming job reads messages from Pub/Sub

4.Messages are transformed into BigQuery-compatible rows

5.Valid records are written into BigQuery table

6.Failed records (if any) are routed to error handling steps

🧾 BigQuery Schema (Streaming Table)

row_key STRING,
name STRING,
age INT64,
email STRING,
join_date DATE,
last_login DATETIME,
loyalty_points INT64,
account_balance FLOAT64,
is_active BOOL,
inserted_at DATETIME,
updated_at DATETIME,
loyalty_status STRING,
account_age_days INT64

📸 Execution Proof
📊 BigQuery – Query Results

Real-time data successfully streamed and queried from BigQuery.

🔄 Dataflow – Streaming Job Graph (View 1)

End-to-end pipeline showing Pub/Sub ingestion and BigQuery sink.

🔄 Dataflow – Streaming Job Graph (View 2)

Expanded view highlighting successful and failed record handling stages.

📜 Dataflow – Job Logs

Pipeline execution logs showing successful job initialization and runtime behavior.

🧠 Dataflow – Worker Logs

Worker-level logs indicating healthy execution, low latency, and zero data lag.

🧪 Observations & Metrics

Streaming latency: < 1 second

Data lag: 0 seconds

Successful writes to BigQuery

Graceful shutdown using Drain

No data loss during termination

🔐 Security & Cost Management

Service account keys revoked after use

Environment variables cleared

All cloud resources deleted post-testing

No active Pub/Sub, Dataflow, BigQuery, or GCS resources

Zero residual billing

🎯 Learning Outcomes

Designed a real-time streaming architecture on GCP

Understood Pub/Sub topic vs subscription behavior

Implemented schema-driven BigQuery ingestion

Managed Dataflow job lifecycle (run, monitor, drain)

Applied cloud security and cost best practices

🚀 How to Run (High-Level)

Create Pub/Sub topic

Create BigQuery dataset & table

Create BigQuery subscription or Dataflow job

Run Python publisher script

Monitor Dataflow and query BigQuery

📌 Project Status

✔ Completed
✔ Tested
✔ Resources cleaned up

Built a real-time data streaming pipeline using Google Cloud Pub/Sub, Dataflow, and BigQuery; validated ingestion through live Dataflow job graphs, worker logs, and BigQuery query results while following security and cost best practices.

📂 Repository Structure
.
├── publisher.py
├── requirements.txt
├── README.md
└── screenshots/
├── bigquery-query-result.png
├── dataflow-job-graph-1.png
├── dataflow-job-graph-2.png
├── dataflow-job-logs.png
└── dataflow-worker-logs.png

🙌 Final Note

This project focuses on real-world data engineering practices, including streaming ingestion, schema enforcement, monitoring, and responsible cloud cleanup.
