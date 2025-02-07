# Customer Analytics Pipeline

This project implements an **ELT pipeline** using **Apache Airflow, dbt, and Snowflake** to extract customer transactions from PostgreSQL, load them into Snowflake, and transform them into analytics-ready data.

## 🚀 Tech Stack

- **Apache Airflow** → Orchestrates the ELT process
- **dbt (Data Build Tool)** → Transforms raw data into analytics tables
- **Snowflake** → Cloud data warehouse
- **PostgreSQL** → Source database
- **Docker** → Containerized environment

## 📁 Project Structure

```
customer-analytics-pipeline/
│── airflow/  
│   ├── dags/  
│   │   ├── elt_pipeline.py  
│   ├── docker-compose.yml  
│   ├── airflow.cfg  
│── dbt/  
│   ├── models/  
│   │   ├── staging/  
│   │   │   ├── transactions.sql  
│   │   ├── marts/  
│   │   │   ├── customer_revenue.sql  
│   ├── dbt_project.yml  
│   ├── profiles.yml  
│── sql/  
│   ├── create_snowflake_schema.sql  
│   ├── seed_data.sql  
│── docs/  
│   ├── README.md  
│── .env  
│── .gitignore  
│── requirements.txt  
│── setup.sh  
```

## 🛠 Setup Instructions

### 1️⃣ Clone the Repository

```sh
git clone <your-github-repo-url>
cd customer-analytics-pipeline
```

### 2️⃣ Set Up Environment Variables

Create a `.env` file and add the following:

```env
SNOWFLAKE_USER=<your_user>
SNOWFLAKE_PASSWORD=<your_password>
SNOWFLAKE_ACCOUNT=<your_account>
SNOWFLAKE_DATABASE=analytics_db
SNOWFLAKE_WAREHOUSE=compute_wh
POSTGRES_CONN_STRING=postgresql://user:password@host:5432/dbname
```

### 3️⃣ Start Airflow with Docker

```sh
docker-compose up -d
```

### 4️⃣ Run dbt Setup

```sh
cd dbt
pip install -r requirements.txt
dbt debug
dbt run
```

### 5️⃣ Trigger Airflow DAG

- Open Airflow UI at `http://localhost:8080`
- Trigger the `elt_pipeline` DAG manually

## 📊 Expected Output

1. **Raw transactions** in `raw.transactions`
2. **Transformed customer revenue data** in `analytics.customer_revenue`
3. **Automated daily updates** with Airflow

## 📌 Next Steps

- Add **S3 as a staging layer**
- Implement **Airflow Sensors for incremental loads**
- Build **Power BI dashboards on Snowflake**

Happy Data Engineering! 🚀

