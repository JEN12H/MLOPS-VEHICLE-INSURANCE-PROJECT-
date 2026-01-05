# MLOPS Vehicle Insurance Project

This repository contains an end-to-end MLOps project for vehicle insurance prediction, featuring a template-style code structure that allows for reusability in further projects. The project demonstrates best practices in machine learning operations, including data ingestion, validation, transformation, model training, evaluation, deployment, and prediction via a web interface.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Data Schema](#data-schema)
- [API Endpoints](#api-endpoints)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

## Overview

This MLOps project implements a machine learning pipeline for predicting vehicle insurance responses based on customer and vehicle data. The system includes:

- Automated data ingestion from MongoDB
- Data validation and preprocessing
- Model training with evaluation
- Model deployment to AWS S3
- Web-based prediction interface using FastAPI
- Comprehensive logging and error handling
- Modular, reusable code structure

## Features

- **Modular Architecture**: Template-style code structure for easy adaptation to other ML projects
- **End-to-End Pipeline**: Complete ML lifecycle from data ingestion to model deployment
- **Cloud Integration**: AWS S3 for model storage and retrieval
- **Database Integration**: MongoDB for data storage
- **Web Interface**: FastAPI-based web application for predictions
- **Containerization Ready**: Dockerfile included for easy deployment
- **Logging and Monitoring**: Comprehensive logging system for debugging and monitoring
- **Data Validation**: Automated data quality checks and schema validation

## Project Structure

```
MLOPS-VEHICLE-INSURANCE-PROJECT-/
├── app.py                          # Main FastAPI application
├── demo.py                         # Demo script
├── Dockerfile                      # Docker configuration
├── LICENSE                         # Project license
├── pyproject.toml                  # Project metadata and dependencies
├── README.md                       # Project documentation
├── requirements.txt                # Python dependencies
├── setup.py                        # Setup script
├── template.py                     # Project structure template
├── artifact/                       # Model artifacts and data
├── config/                         # Configuration files
│   ├── model.yaml                  # Model configuration
│   └── schema.yaml                 # Data schema definition
├── logs/                           # Application logs
├── notebook/                       # Jupyter notebooks
│   ├── data.csv                    # Sample data
│   ├── experiment_notebook.ipynb   # Experiment notebook
│   └── mongodb_demo.ipynb          # MongoDB demo
├── src/                            # Source code
│   ├── __init__.py
│   ├── cloud_storage/              # AWS S3 integration
│   ├── components/                 # ML pipeline components
│   │   ├── data_ingestion.py
│   │   ├── data_transformation.py
│   │   ├── data_validation.py
│   │   ├── model_evaluation.py
│   │   ├── model_pusher.py
│   │   └── model_trainer.py
│   ├── configuration/              # Database and cloud connections
│   ├── constants/                  # Project constants
│   ├── data_access/                # Data access layer
│   ├── entity/                     # Data entities and configurations
│   ├── exception/                  # Custom exceptions
│   ├── logger/                     # Logging utilities
│   ├── pipeline/                   # Training and prediction pipelines
│   └── utils/                      # Utility functions
├── static/                         # Static web assets
│   └── css/
├── templates/                      # HTML templates
│   └── vehicledata.html
└── Vehicle/                        # Virtual environment
```

## Technologies Used

- **Programming Language**: Python 3.x
- **Web Framework**: FastAPI
- **Machine Learning**: scikit-learn, imbalanced-learn
- **Data Processing**: pandas, numpy
- **Visualization**: matplotlib, plotly, seaborn
- **Database**: MongoDB
- **Cloud Storage**: AWS S3 (boto3)
- **Containerization**: Docker
- **Templating**: Jinja2
- **ASGI Server**: Uvicorn
- **Configuration**: PyYAML

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/MLOPS-VEHICLE-INSURANCE-PROJECT-.git
   cd MLOPS-VEHICLE-INSURANCE-PROJECT-
   ```

2. **Create a virtual environment**:
   ```bash
   python -m venv Vehicle
   source Vehicle/bin/activate  # On Windows: Vehicle\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**:
   Create a `.env` file or set environment variables for:
   - `MONGODB_URL`: MongoDB connection URL
   - AWS credentials for S3 access

## Usage

### Training the Model

Run the training pipeline:
```bash
python app.py
```
Navigate to `http://localhost:8080/train` to trigger model training.

### Making Predictions

1. Start the web application:
   ```bash
   python app.py
   ```

2. Open your browser and go to `http://localhost:8080`

3. Fill in the vehicle and customer data in the form

4. Submit the form to get a prediction (Response-Yes or Response-No)

### Using the Prediction API

You can also use the API directly:
```python
import requests

# Example prediction request
data = {
    "Gender": 1,
    "Age": 25,
    "Driving_License": 1,
    "Region_Code": 28.0,
    "Previously_Insured": 0,
    "Annual_Premium": 2630.0,
    "Policy_Sales_Channel": 152.0,
    "Vintage": 16,
    "Vehicle_Age_lt_1_Year": 0,
    "Vehicle_Age_gt_2_Years": 1,
    "Vehicle_Damage_Yes": 1
}

response = requests.post("http://localhost:8080/", data=data)
print(response.json())
```

## Configuration

### Data Schema

The project uses a predefined schema for vehicle insurance data:

- **Numerical Columns**: Age, Driving_License, Region_Code, Previously_Insured, Annual_Premium, Policy_Sales_Channel, Vintage, Response
- **Categorical Columns**: Gender, Vehicle_Age, Vehicle_Damage
- **Target Column**: Response (0 or 1)

### Model Configuration

Model hyperparameters and settings can be configured in `config/model.yaml`.

### Database Configuration

- Database Name: Proj1
- Collection Name: Proj1-Data
- MongoDB URL: Set via environment variable `MONGODB_URL`

## API Endpoints

- `GET /`: Render the main prediction form
- `POST /`: Submit form data and get prediction
- `GET /train`: Trigger model training pipeline

## Deployment

### Using Docker

1. Build the Docker image:
   ```bash
   docker build -t vehicle-insurance-mlops .
   ```

2. Run the container:
   ```bash
   docker run -p 8080:8080 vehicle-insurance-mlops
   ```

### Cloud Deployment

The project is designed for deployment on cloud platforms like AWS, Azure, or GCP with appropriate modifications to the cloud storage and database configurations.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Jenish Kharva**
- Email: 22aikha028@ldce.ac.in
- GitHub: [your-github-username](https://github.com/your-github-username)

---

*This project serves as a template for building end-to-end MLOps solutions. Feel free to adapt and extend it for your specific use cases.*
