# 🌦 WeatherStack Data Pipeline

An end-to-end Data Engineering pipeline using PostgreSQL, Airflow, dbt, and Superset to ingest, transform, and visualize weather data from the OpenWeather API.

## 🚀 Project Overview

This pipeline performs the following steps:

- 📡 Fetches weather data from the OpenWeather API
- 💾 Stores raw data in PostgreSQL
- 🔄 Transforms data with dbt
- 📊 Visualizes analytics in Superset
- ⚙️ Automates the full workflow with Airflow

## 🧰 Tech Stack

| Tool | Purpose |
|---|---|
| PostgreSQL | Data storage |
| Airflow | Orchestration |
| dbt | Data transformation |
| Superset | Data visualization |
| Docker | Containerization |

## ⚙️ How It Works

### 1) Extract

Airflow DAG tasks:

- Call the OpenWeather API
- Fetch weather fields (temperature, humidity, wind speed, etc.)
- Insert raw data into PostgreSQL

### 2) Transform

dbt models:

- Clean raw data
- Handle null values
- Aggregate metrics (average temperature, daily summaries, etc.)
- Build analytics-ready tables

### 3) Load & Visualize

Superset connects to the PostgreSQL analytics schema to create dashboards such as:

- Daily temperature trends
- Humidity comparison
- Wind speed analysis
- Weather condition distribution

## 🐳 Running the Project (Docker)

### 1) Clone the repository

```bash
git clone https://github.com/DOPHUCDAT/WeatherStack-Datapipeline.git
cd WeatherStack-Datapipeline
```

### 2) Add environment variables

Create a `.env` file:

```env
OPENWEATHER_API_KEY=your_api_key
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=weather_db
```

### 3) Start services

```bash
docker-compose up -d
```

Services:

- Airflow: http://localhost:8080
- Superset: http://localhost:8088
- PostgreSQL: localhost:5432

## 📊 Example Dashboards

Superset dashboards may include:

- 🌡 Average temperature by city
- 📅 Daily weather trend
- 💧 Humidity distribution
- 🌬 Wind speed analysis

## 🔄 Airflow Automation

The Airflow DAG automates:

- API extraction
- Data loading into PostgreSQL
- `dbt run`
- `dbt test`


## 🧪 dbt Models

Typical transformation layers:

- Staging layer (`stg_weather`)
- Intermediate layer
- Mart layer (`fact_weather_daily`)

Run dbt manually:

```bash
docker exec -it dbt_container dbt run
```

## 📈 Data Flow Layers

| Layer | Description |
|---|---|
| Raw | Direct API ingestion |
| Staging | Cleaned and structured tables |
| Mart | Aggregated analytical tables |

## 🎯 Key Learning Outcomes

- Building a production-style ELT pipeline
- Data modeling with dbt
- Workflow orchestration with Airflow
- BI visualization with Superset
- Containerized data stack using Docker
