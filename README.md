# ❄️ Real-Time Sales Data Pipeline: S3 → Snowflake → Tableau

This project demonstrates a **real-time data ingestion pipeline** using **Amazon S3**, **Snowflake**, and **Snowpipe**, culminating in a **live dashboard** built with **Tableau**.

📊 **[View Final Dashboard on Tableau Public →](https://public.tableau.com/app/profile/shaun.kirthan/viz/Book2_17131246219240/Dashboard1)**

## 🧩 Architecture Overview

```mermaid
flowchart TD
  A[S3 Bucket (CSV Upload)] --> B[SQS Notification]
  B --> C[Snowpipe in Snowflake]
  C --> D[Sales Data Table]
  D --> E[Live Tableau Dashboard]
```

## 📁 Folder Structure

```
real-time-sales-data-pipeline/
├── README.md
├── setup.sql
├── sample_sales_data.xlsx
└── docs/
    └── architecture_diagram.png
```

## 🚀 Key Components

### 🔹 Amazon S3
- Stores incoming sales data in `.csv` format
- Triggers an event every time a new file is uploaded via S3 Event Notifications

### 🔹 Snowflake
- `STORAGE INTEGRATION` securely connects to S3
- `STAGE` reads data directly from the bucket
- `FILE FORMAT` parses CSV format correctly
- `TABLE` holds structured sales data
- `SNOWPIPE` listens for new files and ingests them automatically

### 🔹 Tableau
- Connected live to the `sales_data` table in Snowflake
- Provides interactive dashboards visualizing the ingested data

## 📄 Dataset

A synthetic dataset with 1,000 sales records containing:

- `order_id`
- `customer_name`
- `product`
- `price`
- `date`

## 🧪 Implementation Steps

### ✅ Snowflake Setup

1. Created a **Storage Integration** to securely access S3
2. Created a **Stage** pointing to the S3 bucket
3. Defined a **File Format** to interpret CSV structure
4. Created a **sales_data table** to store ingested data
5. Built a **Snowpipe** for automated ingestion triggered by S3 file uploads
6. Configured **S3 → SQS notifications** to notify Snowpipe
7. **Manually loaded historical data** using `COPY INTO` for initial setup

> 💡 **Why:** This setup removes manual steps and enables automated, near real-time ingestion of structured sales data.

### 📈 Tableau Integration

- Connected Tableau to Snowflake's `sales_data` table
- Built an interactive dashboard to visualize:
  - Sales volume over time
  - Most purchased products
  - Top customers and trends
- Published to Tableau Public for sharing and access

🔗 **[Live Dashboard](https://public.tableau.com/app/profile/shaun.kirthan/viz/Book2_17131246219240/Dashboard1)**

## 🛠️ Technologies Used

- **Snowflake** – Cloud Data Warehouse with Snowpipe
- **Amazon S3** – Object Storage
- **Amazon SQS** – Notification Service
- **Tableau** – Business Intelligence & Dashboards
- **Python & Faker** – For dataset generation
- **SQL** – For setup and data loading

## 📌 Project Benefits

- Automates the data pipeline
- Demonstrates real-world event-driven ingestion
- Eliminates manual file handling
- Ends with clean, interactive visualizations
- Fully cloud-native and scalable

## 🔄 Future Enhancements

- Add data validation or cleanup via **Snowflake Streams or Tasks**
- Enable logging of ingestion events for auditing
- Expand to multi-region S3 ingestion support
- Use **Apache Airflow** for full pipeline orchestration

## 🙋‍♂️ Author

**Shaun Kirthan**  
M.S. in Data Analytics Engineering, Northeastern University  
🔗 [LinkedIn](https://linkedin.com/in/shaunkirthan) | Data Engineer passionate about cloud pipelines, analytics, and automation
