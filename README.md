# ❄️ Real-Time Sales Data Pipeline: S3 → Snowflake → Tableau

This project demonstrates a **real-time data ingestion pipeline** using **Amazon S3**, **Snowflake**, and **Snowpipe**, culminating in a **live dashboard** built with **Tableau**.

📊 **[View Final Dashboard on Tableau Public →](https://public.tableau.com/app/profile/shaun.kirthan/viz/Book2_17131246219240/Dashboard1)**

---

## 🧩 Architecture Overview

```mermaid
graph TD;
  A[S3 Bucket (CSV Upload)] -->|Auto-trigger| B(SQS Notification);
  B --> C[Snowpipe in Snowflake];
  C --> D{Sales Data Table};
  D --> E[Live Tableau Dashboard];
```

---

## 🚀 Key Components

### 🔹 Amazon S3
- Stores incoming sales data in `.csv` format.
- Triggers an event every time a new file is uploaded via S3 Event Notifications.

### 🔹 Snowflake
- `STORAGE INTEGRATION` securely connects to S3.
- `STAGE` references the S3 bucket.
- `FILE FORMAT` defines CSV parsing rules.
- `TABLE` stores the structured, queryable sales data.
- `SNOWPIPE` auto-ingests files upon upload using SQS notifications.

### 🔹 Tableau
- Connects live to the Snowflake `sales_data` table.
- Visualizes sales insights like trends, products, and customer behaviors.

---

## 📄 Dataset

A synthetic dataset with 1,000 rows and the following columns:

- `order_id`
- `customer_name`
- `product`
- `price`
- `date`

📁 **[Download sample_sales_data.xlsx](sandbox:/mnt/data/sample_sales_data.xlsx)**

---

## 🧪 What I Did – Step-by-Step

### ✅ Snowflake Setup

1. Created a **secure S3 integration** using `STORAGE_INTEGRATION`.
2. Defined a **Stage** that references the S3 bucket.
3. Created a **table** (`sales_data`) to store ingested records.
4. Built a **file format** with CSV rules (delimiter, skip headers, null handling).
5. Created a **Snowpipe** for **auto-ingestion** of new S3 files.
6. Configured **S3 Event Notifications** to send `PUT` events to **SQS**.
7. **Manually loaded historical data** using `COPY INTO`.

> 💡 **Why**: This enables a **scalable, near real-time ingestion pipeline** that requires no manual file processing.

---

### 📈 Tableau Integration

- Connected Tableau directly to the Snowflake `sales_data` table.
- Built an interactive dashboard to analyze:
  - 📅 Sales over time
  - 📦 Product performance
  - 👤 Customer trends
- Published the dashboard to Tableau Public.

🔗 **[Live Dashboard](https://public.tableau.com/app/profile/shaun.kirthan/viz/Book2_17131246219240/Dashboard1)**

---

## 🛠️ Technologies Used

- **Snowflake** – Cloud data warehouse, Snowpipe automation
- **Amazon S3 + SQS** – Object storage and event-driven triggers
- **Tableau** – Interactive BI and dashboarding
- **Python & Faker** – Sample data generation
- **SQL** – Table, Stage, Snowpipe configuration

---

## 📌 Why This Project Matters

✅ Real-world pipelines rarely involve manual imports  
✅ Snowpipe showcases **event-driven automation**  
✅ Tableau proves the **end-to-end flow** from raw data to insight  
✅ It's **cloud-native**, **scalable**, and **production-ready**

---

## 🔄 Future Enhancements

- Add data quality checks with **Snowflake Tasks or Streams**
- Maintain audit logs of ingestions
- Support **multi-region S3 buckets**
- Orchestrate full pipeline with **Apache Airflow**

---

## 🙋‍♂️ Author

**Shaun Kirthan**  
M.S. in Data Analytics Engineering, Northeastern University  
🔗 [LinkedIn](#) | 🧠 Passionate about cloud data pipelines, automation, and analytics

---
```

---

### ✅ Next Steps

Let me know if you'd like:
- A `.zip` file with everything (`README.md`, sample Excel, SQL setup)
- An image version of the architecture diagram
- A Markdown-to-PDF version for resume/portfolio
- Help turning this into a blog or LinkedIn post

You're all set to showcase this on GitHub or as a portfolio project!
