
# EthioMedDataWarehouse 📊🏥

## Overview 🌍

The **EthioMedDataWarehouse** project is designed to collect, clean, process, and analyze data related to Ethiopian medical businesses from various online sources like websites and Telegram channels. The project also incorporates **Object Detection using YOLO** (You Only Look Once) to enhance data analysis capabilities. The final product is a robust **data warehouse** that facilitates comprehensive reporting and insights into the Ethiopian medical sector.

## Business Need 📈

This project was initiated by **Kara Solutions**, a leading data science company with over 50+ data-centric solutions, to build a scalable data warehouse for storing and analyzing Ethiopian medical business data. The data warehouse will support insights on trends and patterns in the medical field by processing data scraped from Telegram channels and web sources. Additionally, object detection using **YOLO** will be integrated to help identify specific elements within collected image data.

## Key Features 🧑‍⚕️🧑‍💻

### Data Scraping and Collection Pipeline 🕵️‍♂️

- Scrape data from public **Telegram channels** related to Ethiopian medical businesses using Python packages such as **Telethon**, **Scrapy**, and **Selenium**.
- Collect images for **object detection** using YOLO.

### Data Cleaning and Transformation 🧹

- Clean and transform raw data using **ETL** (Extract, Transform, Load) and **ELT** (Extract, Load, Transform) processes.
- Use **DBT** (Data Build Tool) for data transformation and ensuring data consistency.

### Object Detection with YOLO 🎯

- Integrate **YOLO** for **object detection** within images collected from Telegram channels.
- Store and analyze object detection data for business insights.

### Data Warehouse Design and Implementation 🏢

- Design a scalable data warehouse to support efficient querying and reporting.
- Store cleaned and transformed data in a relational database (**PostgreSQL**).

### Data Integration and Enrichment 🔗

- Enrich scraped data by integrating multiple data sources.
- Implement pipelines to continuously update the data warehouse.

## Tech Stack 🛠️

- **Python** (Pandas, Telethon, Scrapy, Selenium)
- **YOLO** for Object Detection (TensorFlow, PyTorch, OpenCV)
- **PostgreSQL** for Data Warehouse
- **DBT** for Data Transformation
- **FastAPI** for Exposing APIs
- **Docker** for Containerization
- **SQLAlchemy** for Database Integration
- **Uvicorn** for ASGI Server

## Installation 🧰

### Clone the Repository

```bash
git clone https://github.com/jonnahjr/EthioMedDataWarehouse.git
cd EthioMedDataWarehouse
```

### Install Dependencies

You will need to install the required dependencies for data scraping, processing, and object detection.

```bash
pip install -r requirements.txt
```

### Set Up Database

Make sure you have **PostgreSQL** installed and create a new database for the project. Update the `database.py` file with your database credentials.

```bash
CREATE DATABASE med_data_warehouse;
```

### Set Up YOLO Environment

Clone the **YOLOv5** repository and install the necessary dependencies.

```bash
git clone https://github.com/ultralytics/yolov5.git
cd yolov5
pip install -r requirements.txt
```

### Running the Project 🚀

You can run individual scripts for different tasks (scraping, data processing, etc.) or run the full pipeline end-to-end.

```bash
python src/scraping/telegram_scraper.py
python src/object_detection/yolo_object_detection.py
```

## Project Structure 📁

```bash
├── app/
│   ├── telegram_scraper.py     # Script for scraping Telegram data
│   ├── utils.py                # Helper functions for scraping
│   └── raw_data/               # Directory where raw data is temporarily stored
├── data/
│   ├── dbt_project/            # DBT models for data transformation
│   └── cleaning_pipeline.py    # Script for running DBT data cleaning models
├── images/
│   ├── detect.py               # Script for YOLO object detection
│   └── images/                 # Scraped images for object detection
├── logs/
│   ├── main.py                 # FastAPI app entry point
│   ├── crud.py                 # CRUD operations for API
│   ├── schemas.py              # Pydantic schemas for request/response validation
│   └── database.py             # Database connection for FastAPI
│   └── models.py               # SQLAlchemy models for the data warehouse
├── medical_data/
│   ├── telegram_scraper.py     # Script for scraping Telegram data
│   ├── utils.py                # Helper functions for scraping
│   └── raw_data/               # Directory where raw data is temporarily stored
├── notebooks/
│   ├── dbt_project/            # DBT models for data transformation
│   └── cleaning_pipeline.py    # Script for running DBT data cleaning models
├── scripts/
│   ├── detect.py               # Script for YOLO object detection
│   └── images/                 # Scraped images for object detection
├── src/
│   ├── main.py                 # FastAPI app entry point
│   ├── crud.py                 # CRUD operations for API
│   ├── schemas.py              # Pydantic schemas for request/response validation
│   └── database.py             # Database connection for FastAPI
│   └── models.py               # SQLAlchemy models for the data warehouse
├── tests/
│   ├── telegram_scraper.py     # Script for scraping Telegram data
│   ├── utils.py                # Helper functions for scraping
│   └── raw_data/               # Directory where raw data is temporarily stored
├── yolov5/
│   ├── dbt_project/            # DBT models for data transformation
│   └── cleaning_pipeline.py
├── .gitignore               
├── requirements.txt
└── README.md                   
```

## Usage 🏃‍♂️

### Telegram Channels Scraped 📱

- [DoctorsET](https://t.me/DoctorsET)
- [Chemed Telegram Channel](https://t.me/lobelia4cosmetics)
- [Yetenaweg](https://t.me/yetenaweg)
- [EAHCI](https://t.me/EAHCI)
- Additional channels from [https://et.tgstat.com/medicine](https://et.tgstat.com/medicine)

### Setup and Execution

1. **Install Dependencies**:

   ```bash
   pip install telethon
   ```

2. **Telegram Scraping**: Before running, make sure to create a `.env` file with your **Telegram API** credentials (API ID, API hash, and phone number).

   Example `.env` file:

   ```plaintext
   API_ID=your_api_id
   API_HASH=your_api_hash
   PHONE=your_phone_number
   ```

   - Run `src/scraping/telegram_scraper.py` to collect data from specified Telegram channels.

3. **Data Cleaning and Transformation**: After scraping, the raw data is cleaned and transformed using **DBT** (Data Build Tool). This process involves removing duplicates, handling missing values, and standardizing formats for easy querying and analysis.

#### Setup and Execution

1. **Install DBT**:

   Install DBT and initialize a new DBT project:

   ```bash
   pip install dbt
   dbt init medical_data
   ```

2. **Define DBT Models**:
   - Define SQL models in the `medical_data/models/` directory for cleaning and transforming data.
   - Sample DBT model file:

     ```sql
     -- models/cleaned_telegram_data.sql
     select
         distinct message_id,
         message_text,
         timestamp::timestamp as message_time,
         channel_name
     from raw_data
     where message_text is not null
     ```

3. **Run DBT Models**:

   Apply the transformations by running the DBT models:

   ```bash
   dbt run
   ```

4. **Testing**:

   Test data quality using DBT's built-in test features:

   ```bash
   dbt test
   ```

### 3. Object Detection using YOLO 🧑‍💻🎯

#### Description

In this task, we perform **object detection** on the scraped images using **YOLOv5** to detect medical equipment, promotional materials, and other objects related to Ethiopian medical businesses.

#### Setup and Execution

1. **Install YOLO Dependencies**:

   Install **PyTorch** and **YOLOv5**:

   ```bash
   pip install torch torchvision
   git clone https://github.com/ultralytics/yolov5.git
   cd yolov5
   pip install -r requirements.txt
   ```

2. **Prepare Images**:

   Place the scraped images from the `images/` folder directory for object detection.

3. **Run YOLO**:

   Run the YOLOv5 object detection script:

   ```bash
   cd yolov5
   python detect.py --weights yolov5s.pt --img 640 --conf 0.5 --source data/images
   ```

4. **Store Detection Results**:

   The detection results (bounding boxes, class labels, and confidence scores) will be saved in a structured format, which will later be loaded into the data warehouse.

### 4. Data Warehouse Design and Implementation 🏢

#### Description

The data warehouse stores all the cleaned, transformed, and enriched data, enabling efficient querying and analysis. The data includes textual Telegram posts, image metadata, and YOLO object detection results.

#### Setup and Execution

1. **Install PostgreSQL**:

   Install and configure **PostgreSQL**, or alternatively, use **SQLite** for local testing.

2. **Database Models**:

   Define your database schema in `app/models.py` using **SQLAlchemy**:

   ```python
   from sqlalchemy import Column, Integer, String, ForeignKey
   from sqlalchemy.orm import relationship

   class ImageMetadata(Base):
       __tablename__ = 'image_metadata'
       id = Column(Integer, primary_key=True)
       image_path = Column(String, nullable=False)
       channel_name = Column(String, nullable=False)
       timestamp = Column(String, nullable=False)

   class ObjectDetection(Base):
       __tablename__ = 'object_detection'
       id = Column(Integer, primary_key=True)
       image_id = Column(Integer, ForeignKey('image_metadata.id'))
       label = Column(String, nullable=False)
       confidence = Column(Float, nullable=False)
       detected_at = Column(String, nullable=False)
   ```

3. **Run Migrations**:

   ```bash
   alembic upgrade head
   ```

4. **Query Data**:

   Use **SQLAlchemy** to query and retrieve data for analysis.

## Author 👨‍💻

**yonas bogale sitotaw**  
GitHub: [https://github.com/jonnahjr](https://github.com/jonnahjr)  
LinkedIn: [https://www.linkedin.com/in/jonnahjr](https://www.linkedin.com/in/jonnahjr)  
Email: [jonasjjonas14@gmail.com](mailto:jonasjjonas14@gmail.com)
```
