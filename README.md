# microsoft-fabric-environmental-monitoring

A cloud-based data engineering project that ingests, processes, and visualizes real-time weather and air quality data using Microsoft Fabric.

## 🎯 Project Overview

End-to-end data pipeline that collects environmental data from multiple global cities, processes it through a medallion architecture, and delivers actionable insights via interactive dashboards.

## 🏗️ Architecture
<img width="389" height="313" alt="image" src="https://github.com/user-attachments/assets/e56ae2bb-f779-4b10-8a68-df80ac11bc9f" />

## 🛠️ Tech Stack

- **Cloud Platform:** Microsoft Fabric
- **Data Processing:** PySpark, Python
- **Storage:** Delta Lake (Lakehouse)
- **Orchestration:** Azure Data Factory
- **Visualization:** Power BI
- **Data Source:** REST APIs (OpenWeather)

<img width="523" height="176" alt="image" src="https://github.com/user-attachments/assets/2cc7ab04-7f29-41d6-834a-e87d7ae5389b" />


## 🚀 Features

- ✅ **Automated hourly data refresh** from live APIs
- ✅ **Medallion architecture** (Bronze → Silver → Gold)
- ✅ **10+ global cities** monitored
- ✅ **Real-time air quality tracking** (AQI, PM2.5, PM10)
- ✅ **Interactive dashboards** with 15+ visualizations
- ✅ **Error handling** and retry logic
- ✅ **Scalable Delta Lake storage**

## 📊 Data Pipeline

### 1. Data Ingestion (Bronze Layer)
- Fetches weather and air quality data via REST APIs
- Stores raw JSON responses with timestamps
- Handles authentication and rate limiting

### 2. Data Transformation (Silver Layer)
- Flattens nested JSON structures
- Standardizes data types and units
- Removes duplicates and validates quality
- Creates two Delta tables: `silver_weather` and `silver_air_quality`

### 3. Analytics Layer (Gold Layer)
- Joins weather and air quality data
- Creates aggregated views by country
- Generates city rankings by air quality
- Produces executive summary metrics

## 🎨 Dashboard Features

**Page 1: Global Overview**
- KPI cards (temperature, air quality, city count)
- Interactive global map
- City details table
- Air quality distribution chart

**Page 2: Temperature Analysis**
- Country-wise temperature comparison
- Humidity trends
- Temperature alerts

**Page 3: Air Quality Rankings**
- City rankings by AQI
- Pollutant concentration charts (PM2.5, PM10, CO, NO2)
- Regional air quality breakdown

## ⚙️ Setup Instructions

### Prerequisites
- Microsoft Fabric workspace (Trial/Paid)
- OpenWeather API key ([Get free key](https://openweathermap.org/api))

### Steps

1. **Create Lakehouse**
   - In Fabric workspace, create new Lakehouse: `environmental_lakehouse`
   - Create folder structure: `bronze/weather`, `bronze/air_quality`, `silver`, `gold`

2. **Import Notebooks**
   - Upload notebooks from `/notebooks` folder
   - Attach to the lakehouse

3. **Configure API Key**
   - Open `01_ingest_weather_data.ipynb`
   - Replace `YOUR_API_KEY_HERE` with your OpenWeather API key

4. **Run Notebooks**
   - Execute notebooks in sequence (01 → 02 → 03)

5. **Create Pipeline**
   - Import `master_environmental_pipeline.json`
   - Configure hourly trigger

6. **Deploy Dashboard**
   - Import `Environmental_Analytics_Dashboard.pbix`
   - Connect to lakehouse tables
   - Publish to workspace

## 📈 Sample Outputs

**Data Volume:**
- 10 cities monitored
- 240 records/day (hourly updates)
- 7,200 records/month

**Tables Created:**
- `silver_weather` (cleaned weather data)
- `silver_air_quality` (cleaned air quality data)
- `gold_city_metrics` (joined comprehensive view)
- `gold_temperature_analysis` (country aggregations)
- `gold_air_quality_rankings` (sorted by AQI)
- `gold_executive_summary` (global KPIs)

## 🔄 Automation

Pipeline runs **every hour** automatically:
1. Fetch fresh API data
2. Process Bronze → Silver → Gold
3. Power BI dashboard auto-refreshes

## 🌍 Cities Monitored

London (UK), New York (US), Tokyo (JP), Mumbai (IN), Paris (FR), Sydney (AU), Toronto (CA), Berlin (DE), Singapore (SG), Dubai (AE)

## 🎯 Use Cases

- Urban planning and smart city initiatives
- Healthcare risk assessment (pollution impact)
- Logistics route optimization
- Government environmental monitoring
- Public awareness dashboards

## 🔧 Key Learnings

- REST API integration with authentication
- PySpark for distributed data processing
- Delta Lake for ACID transactions
- Medallion architecture implementation
- Cloud data pipeline orchestration
- Power BI dashboard design

## 📝 Future Enhancements

- [ ] Add machine learning for weather forecasting
- [ ] Implement streaming with Event Hubs
- [ ] Add Great Expectations for data quality
- [ ] Expand to 50+ cities
- [ ] Include historical trend analysis (90+ days)
- [ ] Add email alerts for extreme conditions

## 📄 License

This project is for educational and portfolio purposes.

## 👤 Author

Nikita Kulkarni  
www.linkedin.com/in/nikitakulkarni32


## 🙏 Acknowledgments

- OpenWeather API for data access
- Microsoft Fabric documentation

**Note:** API keys and sensitive credentials are not included in this repository. Configure your own keys before running.

