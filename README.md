# ❄️ Real-Time Sales Data Pipeline: S3 → Snowflake → Tableau

This project demonstrates a **real-time data ingestion pipeline** using **Amazon S3**, **Snowflake**, and **Snowpipe**, culminating in a **live dashboard** built with **Tableau**. 

📊 [View Final Dashboard on Tableau Public »](https://public.tableau.com/app/profile/shaun.kirthan/viz/Book2_17131246219240/Dashboard1)

---

## 🧩 Architecture Overview

```mermaid
graph TD
  A[S3 Bucket (CSV Upload)] -->|Auto-trigger| B(SQS Notification)
  B --> C(Snowpipe in Snowflake)
  C --> D{Sales Data Table}
  D --> E[Live Tableau Dashboard]
🚀 Key Components
🔹 Amazon S3
Stores incoming sales data in .csv format.

Triggers an event every time a new file is uploaded.

🔹 Snowflake
Storage Integration securely connects to S3.

Stage reads raw data from S3.

Snowpipe ingests data automatically on file upload.

Table stores structured, queryable data.

File Format ensures correct parsing of the CSV.

🔹 Tableau
Connects to Snowflake as a live data source.

Creates interactive visualizations using ingested data.

📄 Dataset
A synthetic dataset with 1,000 sales records. Sample columns include:

order_id

customer_name

product

price

date

📁 Download sample_sales_data.xlsx

🧪 Steps & What I Did
✅ Snowflake Setup
Created a secure S3 integration using STORAGE_INTEGRATION.

Defined a Stage to point to the bucket using that integration.

Created a table to store structured sales data.

Defined a CSV file format that matches incoming files.

Built a Snowpipe to enable auto-ingestion from S3.

Set up S3 Event Notifications (via SQS) to trigger the pipe.

Manually loaded historical data once using COPY INTO.

✅ Why: This pipeline eliminates manual uploads and ensures scalable, near real-time ingestion of sales data with minimal operational overhead.

📈 Tableau Integration
Connected Tableau directly to the Snowflake sales_data table.

Built an interactive dashboard tracking:

Sales volume over time

Product popularity

Customer purchasing trends

Published the dashboard to Tableau Public.

🔗 Live Dashboard

🛠️ Technologies Used
Snowflake: Data warehouse, Snowpipe automation

Amazon S3 + SQS: Object storage and trigger system

Tableau: BI and dashboarding

Python & Faker: For generating sample datasets

SQL: For pipeline configuration and data management

📌 Why This Project Matters
✅ Real-world pipelines rarely involve manual imports.
✅ Snowpipe showcases event-driven automation.
✅ Tableau integration proves the end-to-end flow, from raw data to insights.
✅ It's cloud-native, scalable, and production-worthy.

🔄 Future Enhancements
Add data quality checks using Snowflake Tasks or Streams.

Log ingestion events for auditing.

Scale to multi-region S3 bucket ingestion.

Integrate with Apache Airflow for orchestrated workflows.
