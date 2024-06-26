# AIR Quality Data Project

### Problem Statement
The project aims to establish an end-to-end data pipeline for extracting air quality data from APIs, transforming it, and storing it in a data lake or warehouse. The pipeline will enable visualization for tracking trends and statistical insights, facilitating informed decision-making regarding environmental conditions.

The Air Quality Index (AQI) is used for reporting daily air quality. It tells you how clean or polluted your air is, and what associated health effects might be a concern for you. The AQI focuses on health effects you may experience within a few hours or days after breathing polluted air.
- **AQI Level and Recommendations**

| AQI Range | Air Quality | Health Implications       | Recommendations                               |
|-----------|-------------|---------------------------|-----------------------------------------------|
| 0 - 50    | Good        | Little to no risk         | None                                          |
| 51 - 100  | Moderate    | Slight risk for sensitive individuals | Limit outdoor activity for sensitive groups |
| 101 - 150 | Unhealthy for Sensitive Groups | Risk for sensitive groups | Limit outdoor activity for sensitive groups |
| 151 - 200 | Unhealthy   | Risk for everyone         | Avoid prolonged outdoor activity             |
| 201 - 300 | Very Unhealthy | Emergency conditions  | Avoid outdoor activity                        |
| 300+      | Hazardous   | Severe health effects     | Avoid all outdoor activity                   |


### Pipeline Execution (DAG)
- The DAG updates every 20 minutes to ensure data remains up-to-date. Normally, data is scheduled to be updated hourly, but occasional delays occur.

### Data Schema

| Column | Type | 
|--------|-------------|
| aqi | int |
| city | str |
| country | str |
| latitude | float |
| longitude | float |
| temperature_c | float |
| humidity_percent | float |
| wind_speed_m_s | float |
| pressure_hpa | float |
| pm25_concentration_ug_per_m3 | float |
| aqi_level | str |

### Data Pipeline

- **Pipeline**

![image](https://github.com/EarthSuppawoot/air-quality/assets/157554832/b7dd2662-9059-4798-95d7-75d083a85c66)

- **DAG**

![image](https://github.com/EarthSuppawoot/air-quality/assets/157554832/9e79aeb0-e7b6-4101-b711-ae52e9294cdd)

### Technologies and Tools
- **Cloud**: Amazon Web Services (AWS)
- **Containerization**: Docker
- **Workflow Orchestration**: Apache Airflow
- **Data Lake**: AWS S3
- **Data Warehousing**: Amazon Redshift
- **Data Visualization**: Power BI
- **Language**: Python


### Analytics Dashboard
The dashboard will have four parts with control filter on time and city that represent the analytics points below:

1. **AQI Time Series Plot**: Shows how air quality changes over time.
2. **AQI Visualization Map**: Displays air quality levels in different cities.
3. **Temperature-AQI Relationship Plot**: Explains how temperature affects air quality.
4. **Distribution by AQI Level**: Illustrates how often different air quality levels occur.
   

   For the live dashboard, I cannot publish Power BI because I don't have any business email. So, here is an example of the dashboard. (The data provided is only for the day that DAG is running.)
   
  
- **Bangkok**
 
![image](https://github.com/EarthSuppawoot/air-quality/assets/157554832/80a00f9e-f7af-472a-933b-ce8c09fc614c)


- **Chiang Mai**

![image](https://github.com/EarthSuppawoot/air-quality/assets/157554832/001b6443-a8b6-4236-86b9-762c7ac35015)


- **Phuket**

![image](https://github.com/EarthSuppawoot/air-quality/assets/157554832/f5334dd9-9ecd-41f9-8392-c727ffa768f2)



### Setup Instructions

1. Setup your AWS account and create s3 bucket
2. Clone the repository to your local machine to get started.
   
   ```bash
   git clone https://github.com/exrrth/data-engineering-zoomcamp-project-2024.git
   ```

3. Modify the DAG file to add more cities of interest. You can edit the DAG file manually.
![image](https://github.com/exrrth/data-engineering-zoomcamp-project-2024/assets/157554832/24b767fc-ec39-4589-988a-a82401ce539a)

4. Run Airflow using Docker to execute the pipeline:

   ```bash
   docker compose up -d --build
   ```

5. Access the Airflow UI at localhost:8080 and log in with credentials (airflow:airflow).
![image](https://github.com/exrrth/data-engineering-zoomcamp-project-2024/assets/157554832/18b1e3a6-afb2-470a-8674-1a5300d2c952)

6. Enable the DAG within the Airflow UI.

7. Verify the data in the AWS S3 bucket.

8. Go to AWS Glue and run the job.
![image](https://github.com/exrrth/data-engineering-zoomcamp-project-2024/assets/157554832/c4d536f6-f9c6-423b-9558-1d00c0b05689)

9. Utilize the AWS Glue crawler to crawl the data.
![image](https://github.com/exrrth/data-engineering-zoomcamp-project-2024/assets/157554832/a5a3ee8b-79b2-4813-937d-5584b357091a)

10. Check the data in the tables within AWS Athena.
![image](https://github.com/exrrth/data-engineering-zoomcamp-project-2024/assets/157554832/a4a928a0-6a1e-4eed-9603-6c1e636d67ca)
![image](https://github.com/exrrth/data-engineering-zoomcamp-project-2024/assets/157554832/a27f7611-80e2-4aa5-9f2c-69c509d60879)

11. To stop your Docker container, use the following command:
   
   ```bash
   docker-compose stop
   ```





