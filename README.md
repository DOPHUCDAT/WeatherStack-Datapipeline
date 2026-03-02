🌦 WeatherStack Data Pipeline

End-to-end Data Engineering pipeline sử dụng PostgreSQL, Airflow, dbt và Superset để thu thập, xử lý và trực quan hóa dữ liệu thời tiết từ OpenWeather API.

🚀 Project Overview

Pipeline này thực hiện:

📡 Gọi dữ liệu từ OpenWeather API

💾 Lưu raw data vào PostgreSQL

🔄 Transform dữ liệu bằng dbt

📊 Trực quan hóa dữ liệu bằng Superset

⚙️ Tự động hóa toàn bộ bằng Airflow

🧰 Tech Stack
Tool	Purpose
PostgreSQL	Data storage
Airflow	Orchestration
dbt	Data transformation
Superset	Data visualization
Docker	Containerization
📂 Project Structure
WeatherStack-Datapipeline/
│
├── airflow/
│   └── dags/
│
├── dbt/
│   ├── models/
│   └── dbt_project.yml
│
├── postgres/
│
├── superset/
│
├── docker-compose.yml
└── README.md
⚙️ How It Works
1️⃣ Extract

Airflow DAG:

Calls OpenWeather API

Fetches weather data (temperature, humidity, wind speed, etc.)

Inserts raw data into PostgreSQL

2️⃣ Transform

dbt models:

Clean raw data

Handle null values

Aggregate metrics (avg temperature, daily summary, etc.)

Create analytical tables

3️⃣ Load & Visualize

Superset connects to PostgreSQL analytics schema:

Daily temperature trends

Humidity comparison

Wind speed analysis

Weather condition distribution

🐳 Running the Project (Docker)
1️⃣ Clone repository
git clone https://github.com/DOPHUCDAT/WeatherStack-Datapipeline.git
cd WeatherStack-Datapipeline
2️⃣ Add Environment Variables

Create .env file:

OPENWEATHER_API_KEY=your_api_key
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=weather_db
3️⃣ Start services
docker-compose up -d

Services available:

Airflow: http://localhost:8080

Superset: http://localhost:8088

PostgreSQL: localhost:5432

📊 Example Dashboards

Superset dashboards may include:

🌡 Average temperature by city

📅 Daily weather trend

💧 Humidity distribution

🌬 Wind speed analysis

🔄 Airflow Automation

Airflow DAG automates:

API extraction

Data loading into Postgres

dbt run

dbt test

Scheduling example:

@daily
🧪 dbt Models

Typical transformations:

Staging layer (stg_weather)

Intermediate layer

Mart layer (fact_weather_daily)

Run dbt manually:

docker exec -it dbt_container dbt run
📈 Data Flow Layers
Layer	Description
Raw	Direct API ingestion
Staging	Cleaned structured tables
Mart	Aggregated analytical tables
🎯 Key Learning Outcomes

Building production-style ELT pipeline

Data modeling with dbt

Workflow orchestration with Airflow

BI visualization with Superset

Containerized data stack using Docker

🔐 Security Notes

API keys stored in .env

.env excluded via .gitignore

No credentials committed to repo
