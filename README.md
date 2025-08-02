# 📦 Real-Time Sales KPI Dashboard using Kafka, Spark, and Streamlit (Dockerized)

This project demonstrates an end-to-end **real-time data pipeline** built and orchestrated locally using **Docker**, where data is streamed, processed, and visualized using:

- **Kafka** (for data ingestion)
- **Spark** (for scheduled KPI transformations)
- **Streamlit** (for interactive dashboards)
- **Cron Jobs** (for scheduled ETL execution)

---

## 🚀 Project Overview

This project simulates a real-world sales analytics pipeline with the following components:

1. **Data Generation & Ingestion**
   - Synthetic data is produced continuously for **4 Kafka topics**: `customers`, `products`, `orders`, and `order_items`.
   - A Kafka **consumer** reads from these topics and writes raw data into corresponding **CSV files** (one per topic).

2. **Scheduled Transformations (ETL)**
   - A **PySpark job** is scheduled via **cron** to run every **10 minutes**.
   - This job reads the raw CSVs, performs data cleaning, joins, and aggregations.
   - Calculates **key business KPIs** and stores them into **KPI CSV files**.

3. **Data Visualization**
   - A **Streamlit dashboard** reads from the KPI CSVs and renders real-time visualizations.
   - Provides an interactive view into core sales metrics and trends.

---

## 🧱 Architecture Diagram

```plaintext
+----------------+       +------------------+       +-----------------+
| Data Producer  | --->  | Kafka Topics     | --->  | Kafka Consumer  |
| (Python Script)|       | (4 topics)       |       | (Writes to CSV) |
+----------------+       +------------------+       +-----------------+
                                                         |
                                                         v
                                             +--------------------------+
                                             | Raw CSVs (1 per topic)   |
                                             +--------------------------+
                                                         |
                                                (Scheduled via cron)
                                                         v
                                             +--------------------------+
                                             | PySpark Transformation   |
                                             | - KPI Calculation        |
                                             | - Joins, Aggregation     |
                                             +--------------------------+
                                                         |
                                                         v
                                            +---------------------------+
                                            | KPI CSVs (1 per metric)   |
                                            +---------------------------+
                                                         |
                                                         v
                                            +---------------------------+
                                            | Streamlit Dashboard       |
                                            | - Real-time Visualization |
                                            +---------------------------+

```
---
## 🛠️ Tech Stack

- Apache Kafka — Real-time message streaming
- Apache Spark (PySpark) — Batch transformations & KPI aggregation
- Streamlit — Dashboard & visualization
- Cron Jobs — ETL orchestration
- Docker & Docker Compose — Local environment orchestration
- Python — Data generation, consumer, transformations

---
## ✅ Features

- Scheduled ETL: Efficient 10-min transformation window using PySpark
- Real-time Data Flow: Kafka-based producer-consumer model
- Live KPI Monitoring: Clean and interactive Streamlit interface
- Fully Dockerized: One command to launch entire stack
