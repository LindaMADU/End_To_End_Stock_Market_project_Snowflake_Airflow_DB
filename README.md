# End-to-End Stock Market Data Pipeline

## The Problem

 Manual download of stock price files, that requires cleaning them up in Excel, and uploading somewhere for the team to query. This takes hours, it's error-prone, and eventually delays decision making.

---

## The Solution

This project builds a fully automated, end-to-end data pipeline that ingests real-time stock market data, stores it, transforms it, and makes it ready to query — without anyone touching it manually.

Here's how it works:

1. **Stock data comes in through Kafka** — a message streaming system that handles high-frequency data.
2. **Airflow orchestrates everything** — it schedules and monitors each step of the pipeline so nothing runs out of order or gets missed.
3. **MinIO acts as a data lake** — raw data lands here first, like a holding area before it gets processed.
4. **DBT transforms the data** — it cleans, reshapes, and models the raw data into something analysts can actually use.
5. **Snowflake is the final destination** — a cloud data warehouse where the clean, structured data lives and can be queried at any time.


---

<p align="left">
  <img src="https://img.shields.io/badge/Apache%20Kafka-231F20?style=for-the-badge&logo=apache-kafka&logoColor=white" alt="Kafka"/>
  <img src="https://img.shields.io/badge/Apache%20Airflow-017CEE?style=for-the-badge&logo=apache-airflow&logoColor=white" alt="Airflow"/>
  <img src="https://img.shields.io/badge/MinIO-C72E49?style=for-the-badge&logo=minio&logoColor=white" alt="MinIO"/>
  <img src="https://img.shields.io/badge/dbt-FF694B?style=for-the-badge&logo=dbt&logoColor=white" alt="DBT"/>
  <img src="https://img.shields.io/badge/Snowflake-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white" alt="Snowflake"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black" alt="Power BI"/>
</p>

---

## Tech Stack

| Tool | Role |
|---|---|
| Apache Kafka | Real-time data streaming |
| Apache Airflow | Pipeline orchestration |
| MinIO | Object storage / data lake |
| DBT | Data transformation |
| Snowflake | Cloud data warehouse |
| Docker | Containerized infrastructure |
| Python | DAGs and pipeline logic |

---

<img width="4724" height="2364" alt="image" src="https://github.com/user-attachments/assets/0e9c202b-efd9-4a41-b593-1c5dfb42b9aa" />



---

## Project Structure

```
├── infra/
│   ├── docker-compose.yml       # Spins up all services locally
│   └── dags/
│       └── minio_to_snowflake.py  # Airflow DAG for the pipeline
├── dbt/                         # DBT models and transformations
├── venv/                        # Python virtual environment
└── README.md
```

---

## Getting Started

**Prerequisites:** Docker Desktop, Python 3.8+, a Snowflake account

**1. Clone the repo**
```bash
git clone https://github.com/LindaMADU/End_To_End_Stock_Market_project_Snowflake_Airflow_DB.git
cd End_To_End_Stock_Market_project_Snowflake_Airflow_DB
```

**2. Start all services**
```bash
cd infra
docker compose up -d
```

**3. Initialize Airflow**
```bash
docker compose exec airflow-scheduler airflow db migrate
docker compose exec airflow-scheduler airflow users create \
  --username admin --password admin \
  --firstname Admin --lastname User \
  --role Admin --email admin@example.com
```

**4. Open the Airflow UI**
```
http://localhost:8080
```

Enable the `minio_to_snowflake` DAG and trigger it manually to run the pipeline.

---

## What You Get at the End

A fully automated pipeline that takes raw stock market data and delivers clean, query-ready tables in Snowflake — on a schedule, with no manual work involved. 
