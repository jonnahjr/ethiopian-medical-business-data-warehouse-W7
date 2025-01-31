# ethiopian medical business data warehouse 📊🏥

## Overview 🌍
The **EthioMedDataWarehouse** project is designed to collect, clean, process, and analyze data related to Ethiopian medical businesses from various online sources like websites 🌐 and Telegram channels 📱. The project also incorporates object detection using **YOLO** (You Only Look Once) to enhance data analysis capabilities 🔍. The final product is a robust data warehouse that facilitates comprehensive reporting 📈 and insights into the Ethiopian medical sector 🏥.

## Business Need 💡
This project was initiated by **Kara Solutions** 🖥️, a leading data science company with over 50+ data-centric solutions, to build a scalable data warehouse for storing and analyzing Ethiopian medical business data. The data warehouse will support insights on trends and patterns in the medical field by processing data scraped from Telegram channels and web sources. Additionally, object detection using YOLO will be integrated to help identify specific elements within collected image data 🖼️.

## Key Features ⚙️
### Data Scraping and Collection Pipeline 🧹
- Scrape data from public **Telegram channels** 📱 related to Ethiopian medical businesses using Python packages such as **Telethon**, **Scrapy**, and **Selenium**.
- Collect images for object detection 📸.

### Data Cleaning and Transformation 🧼🔄
- Clean and transform raw data using **ETL** (Extract, Transform, Load) and **ELT** (Extract, Load, Transform) processes 🔄.
- Use **DBT** (Data Build Tool) for data transformation and ensuring data consistency 🧹.

### Object Detection with YOLO 🕵️‍♂️
- Integrate **YOLO** for object detection within images collected from Telegram channels 🖼️.
- Store and analyze object detection data for business insights 📊.

### Data Warehouse Design and Implementation 🏗️
- Design a scalable data warehouse 🏛️ to support efficient querying and reporting 🧮.
- Store cleaned and transformed data in a relational database (**PostgreSQL**) 🗄️.

### Data Integration and Enrichment 🔗
- Enrich scraped data by integrating multiple data sources 🌐.
- Implement pipelines to continuously update the data warehouse ⏳.

## Tech Stack 🛠️
- **Python** 🐍 (Pandas, Telethon, Scrapy, Selenium)
- **YOLO for Object Detection** 🔍 (TensorFlow, PyTorch, OpenCV)
- **PostgreSQL** 🗄️ for Data Warehouse
- **DBT** for Data Transformation 🔄
- **FastAPI** ⚡ for Exposing APIs
- **Docker** 🐳 for Containerization
- **SQLAlchemy** for Database Integration 🔌
- **Uvicorn** ⚡ for ASGI Server

## Installation ⚙️

### Clone the Repository 🖥️
```bash
git clone https://github.com/yourusername/EthioMedDataWarehouse.git
cd EthioMedDataWarehouse
```

### Install Dependencies 📦
You will need to install the required dependencies for data scraping, processing, and object detection.
```bash
pip install -r requirements.txt
```

### Set Up Database 🗄️
Make sure you have **PostgreSQL** installed and create a new database for the project. Update the `database.py` file with your database credentials.
```bash
CREATE DATABASE med_data_warehouse;
```

### Set Up YOLO Environment 👀
Clone the YOLOv5 repository and install the necessary dependencies.
```bash
git clone https://github.com/ultralytics/yolov5.git
cd yolov5
pip install -r requirements.txt
```

### Running the Project ▶️
You can run individual scripts for different tasks (scraping, data processing, etc.) or run the full pipeline end-to-end.
```bash
python src/scraping/telegram_scraper.py
python src/object_detection/yolo_object_detection.py
```

## Project Structure 📂
```
EthioMedDataWarehouse/
│
├── notebooks/                    # Jupyter Notebooks for experimentation 📓
│   └── exploration.ipynb
│
├── src/                          # Source code for the project 💻
│   ├── scraping/                 # Scripts for scraping data 🧹
│   │   └── telegram_scraper.py
│   │
│   ├── cleaning/                 # Data cleaning scripts 🧼
│   │   └── data_cleaning.py
│   │
│   ├── object_detection/         # YOLO object detection scripts 👀
│   │   └── yolo_object_detection.py
│   │
│   └── warehouse/                # Scripts for data warehouse setup 🏛️
│       └── database_setup.py
│
├── tests/                        # Unit and integration tests 🧪
│   └── test_scraping.py
│
├── scripts/                      # Utility and helper scripts ⚙️
│   └── run_pipeline.sh           # Script to run the entire pipeline ▶️
│
├── .github/                      # GitHub Actions for CI/CD 🛠️
│   └── workflows/
│       └── python-app.yml        # Python test workflow 🧪
│
├── .gitignore                    # Files to ignore in Git 🚫
├── README.md                     # Project README 📑
├── requirements.txt              # Python dependencies 📦
└── LICENSE                       # Project License 📝
```

## Usage 📝

### Telegram Scraping 📱:
Run `src/scraping/telegram_scraper.py` to collect data from specified Telegram channels.

### Data Cleaning 🧼:
Execute `src/cleaning/data_cleaning.py` to clean the collected raw data.

### Object Detection 🔍:
Use `src/object_detection/yolo_object_detection.py` to run YOLO on collected images and store the detection results.

### Data Warehouse Setup 🏛️:
Run `src/warehouse/database_setup.py` to set up and configure your PostgreSQL data warehouse.

### API Exposure ⚡:
Start the **FastAPI** server by running:
```bash
uvicorn main:app --reload
```
This will expose the data through RESTful APIs 🌐.

## Contributing 🤝
We welcome contributions! Feel free to submit a pull request or open an issue for any bugs or feature requests 🐞.

### Contributions are welcome! Please follow these steps:
1. Fork the repository 🍴.
2. Create a new branch (`git checkout -b feature-branch`) 🌱.
3. Make your changes and commit them (`git commit -m 'Add new feature'`) ✍️.
4. Push to the branch (`git push origin feature-branch`) 🚀.
5. Open a pull request 📩.

## Author 👨‍💻
- **Yonas Bogale Sitotaw** 👨‍💻
  - GitHub: [@jonnahjr](https://github.com/jonnahjr) 🐙
  - LinkedIn: [Yonas Bogale Sitotaw](https://www.linkedin.com/in/jonnahjr) 🔗
  - Email: [jonasjjonas14@gmail.com](mailto:jonasjjonas14@gmail.com) 📧

## License 📝
This project is licensed under the **MIT License** - see the LICENSE file for details 📄.
```
