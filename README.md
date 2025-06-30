# MLOps Zoomcamp - My Assignments

This repository contains my solutions and assignments for the MLOps Zoomcamp course by DataTalks.Club. Each module of the course is organized into separate directories with their respective assignments, code, and documentation.

## Course Overview

MLOps Zoomcamp is a comprehensive course on Machine Learning Operations (MLOps) covering the full lifecycle of ML projects, from data preparation to model deployment and monitoring.

## Repository Structure

- `01-intro/` 
  - Introduction to MLOps
  - NYC Yellow taxi trip duration prediction model
  - Data preprocessing, feature engineering, and model training
  - Metrics evaluation on training and validation datasets

- `02-experiment-tracking/`
  - Experiment tracking with MLflow
  - Training and hyperparameter tuning for taxi trip duration prediction
  - MLflow model registry and tracking server setup
  - Green Taxi Trip data processing and model optimization

- `03-orchestration/`
  - Workflow orchestration using Prefect
  - End-to-end ML pipeline for NYC taxi trip duration prediction
  - Prefect deployment configuration and scheduling
  - Integration of MLflow with Prefect for model tracking
  - Docker containerization for MLflow and Prefect services

- `04-deployment/`
  - Model deployment strategies
  - Batch inference with Docker
  - Cloud storage integration
  - Orchestrated batch workflow with Prefect
  - Production-ready code for model scoring

- `05-monitoring/`
  - Model monitoring for batch services
  - PostgreSQL for metrics storage
  - Grafana for metrics visualization
  - Evidently AI for data drift detection
  - Dockerized monitoring stack

## Completed Assignments

### Module 1: Introduction to MLOps

In this module, I created a linear regression model to predict the duration of taxi trips in NYC using Yellow Taxi Trip Records from January and February 2023. The assignment involved:

- Loading and exploring Yellow Taxi Trip data
- Computing trip durations and handling outliers
- Implementing one-hot encoding for categorical features
- Training a linear regression model
- Evaluating the model on both training and validation datasets

Tools & Libraries used:
- Python
- Pandas, NumPy
- scikit-learn
- Jupyter notebooks

### Module 2: Experiment Tracking and Model Registry

In this module, I implemented experiment tracking and model management using MLflow. The assignment focused on:

- Setting up MLflow for experiment tracking and model versioning
- Processing NYC Green Taxi Trip data for January to March 2023
- Training RandomForestRegressor models with MLflow autologging
- Running hyperparameter optimization with hyperopt
- Setting up a local MLflow tracking server with SQLite backend
- Managing model lifecycle using MLflow Model Registry
- Evaluating and selecting the best model based on validation metrics

Tools & Libraries used:
- MLflow (version 1.27.0)
- Hyperopt for hyperparameter tuning
- scikit-learn (RandomForestRegressor)
- Pandas, NumPy
- SQLite for MLflow backend storage

### Module 3: Orchestration and ML Pipelines

In this module, I implemented workflow orchestration for the NYC taxi trip duration prediction project using Prefect. The work involved:

- Building an end-to-end ML pipeline with Prefect tasks and flows
- Implementing automated data preparation and model training processes
- Setting up Prefect deployments with scheduling capabilities
- Integrating MLflow tracking within the Prefect workflow
- Containerizing the entire workflow with Docker for reproducibility
- Creating monitoring utilities for tracking model performance
- Implementing error handling and retry mechanisms for workflow reliability
- Setting up a complete MLOps environment with both Prefect server and workers

Tools & Libraries used:
- Prefect 3.x for workflow orchestration
- Docker for containerization
- MLflow for experiment tracking
- scikit-learn for modeling
- Shell scripts for automation

### Module 4: Model Deployment

In this module, I implemented batch deployment strategies for the NYC taxi trip duration prediction model. The assignment focused on:

- Converting Jupyter notebooks to production-ready Python scripts
- Building a parameterized batch scoring system for different time periods
- Containerizing the model with Docker for portable execution
- Integrating cloud storage options for prediction results (AWS S3, GCS, Azure)
- Creating an orchestrated batch workflow using Prefect
- Implementing a complete deployment pipeline from data ingestion to result storage
- Designing a flexible system that can handle different data sources and output formats

Tools & Libraries used:
- Docker for containerization
- Prefect for workflow orchestration
- Cloud storage SDKs (boto3, google-cloud-storage)
- pandas for data processing
- scikit-learn for model inference

### Module 5: Model Monitoring

In this module, I implemented a comprehensive monitoring system for ML batch services using NYC Green Taxi data. The assignment involved:

- Setting up a monitoring stack with PostgreSQL, Grafana, and Evidently AI
- Building a baseline linear regression model for taxi trip duration prediction
- Implementing data quality metrics including `QuantileValue` for fare_amount and `ValueDrift` for predictions
- Creating a pipeline to calculate daily metrics for March 2024 data
- Developing a Prefect-orchestrated workflow for metrics calculation
- Storing monitoring metrics in a PostgreSQL database
- Designing custom Grafana dashboards for metric visualization
- Saving and managing dashboard configurations for reproducibility
- Containerizing the entire monitoring stack with Docker

Tools & Libraries used:
- Evidently AI for data quality and model performance monitoring
- PostgreSQL for metrics storage
- Grafana for visualization and alerting
- Docker and Docker Compose for containerization
- Prefect for workflow orchestration
- pandas and scikit-learn for data processing and modeling

## Setup and Installation

This project uses Python 3.10+ and the following dependencies as defined in the `pyproject.toml` file:


The project uses the `uv` package manager for faster dependency resolution and installation:

```bash
# Create a virtual environment using uv
uv venv
source .venv/bin/activate  # On Linux/Mac

# Install dependencies with uv
uv pip install -e .

# The dependencies are locked in the uv.lock file for reproducibility
```

### Module 6: Best Practices

In this module, I implemented MLOps best practices for the NYC taxi trip duration prediction project. The assignment focused on:

- Setting up unit and integration testing with pytest
- Implementing code quality checks with GitHub Actions CI/CD
- Using AWS Lambda for serverless model inference
- Working with LocalStack for local AWS service testing
- Implementing infrastructure as code with Terraform
- Creating Makefile automation for streamlined development workflow
- Establishing a robust project structure with proper package management
- Implementing proper environment management and configuration
- Setting up linting and formatting with isort, black, and pylint
- Creating comprehensive documentation for the project

Tools & Libraries used:
- pytest for testing
- GitHub Actions for CI/CD
- AWS Lambda and LocalStack
- Terraform for infrastructure as code
- Docker and Docker Compose
- Makefile for workflow automation
- isort, black, and pylint for code quality

## Future Work

With all modules completed, the only remaining component is:
- Final Project: Putting all the MLOps practices together in a comprehensive end-to-end solution

## Contact

Feel free to reach out if you have any questions about my assignments or solutions.