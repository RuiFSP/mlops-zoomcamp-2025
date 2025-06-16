# NYC Taxi Trip Duration Prediction - Deployment

This project demonstrates how to deploy a machine learning model for taxi trip duration prediction in various ways:

1. Batch inference with Docker
2. Cloud storage integration
3. Orchestrated workflows with Prefect

## Homework Overview

In this homework, we deployed a ride duration prediction model in batch mode using the NYC Yellow Taxi Trip Records dataset. The main tasks included:

- Converting a Jupyter notebook to a production-ready script
- Parameterizing the script to handle different time periods
- Dockerizing the application
- Extending the solution with cloud storage capabilities
- Using an orchestrator for the batch inference workflow

## Project Structure

```
04-deployment/
│
├── src/                  # Core application code
│   └── scoring.py        # Main scoring script for batch prediction
│
├── orchestration/        # Workflow orchestration with Prefect
│   ├── batch_inference_flow.py  # Prefect flow for batch inference
│   └── deploy.py         # Deployment script for Prefect
│
├── models/               # Model storage
│   └── model.bin         # Pre-trained model
│
├── output/               # Output predictions
│   └── result_yellow_tripdata_*.parquet
│
├── Dockerfile            # Docker configuration for batch inference
├── requirements.txt      # Core dependencies
└── requirements_orchestration.txt  # Dependencies for orchestration
```

## Batch Inference with Docker

### Docker Setup

The solution uses a Docker container with a pre-trained model:

```dockerfile
FROM agrigorev/zoomcamp-model:mlops-2024-3.10.13-slim

WORKDIR /app
COPY [ "requirements.txt", "." ]
RUN pip install -r requirements.txt

COPY [ "src/scoring.py", "." ]

ENTRYPOINT [ "python", "scoring.py" ]
```

### Running the Docker Container

```bash
docker build -t taxi-duration-prediction .
docker run taxi-duration-prediction 2023 05
```

## Cloud Storage Integration

You can extend the solution to upload the prediction results to cloud storage services.

### AWS S3 Integration

```python
import boto3
import os

def upload_to_s3(file_path, bucket_name, object_name=None):
    """Upload a file to an S3 bucket"""
    if object_name is None:
        object_name = os.path.basename(file_path)
        
    # Create S3 client - credentials should be provided via environment variables
    s3_client = boto3.client('s3')
    
    try:
        s3_client.upload_file(file_path, bucket_name, object_name)
        print(f"Successfully uploaded {file_path} to {bucket_name}/{object_name}")
        return True
    except Exception as e:
        print(f"Error uploading to S3: {e}")
        return False
```

### Authentication Setup

Configure cloud provider authentication:

#### AWS S3
```bash
export AWS_ACCESS_KEY_ID=your_access_key
export AWS_SECRET_ACCESS_KEY=your_secret_key
export AWS_DEFAULT_REGION=your_region
```

#### Google Cloud Storage
```bash
export GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account-key.json
```

#### Azure Blob Storage
```bash
export AZURE_STORAGE_CONNECTION_STRING="your_connection_string"
```

## Orchestrated Workflow with Prefect

The orchestrated workflow splits the batch inference process into logical steps:

1. **Data download**: Fetch the latest data
2. **Data preprocessing**: Clean and prepare data for inference
3. **Model loading**: Load the trained model
4. **Batch inference**: Run predictions on the dataset
5. **Result processing**: Format and save the results
6. **Cloud upload**: Upload results to cloud storage
7. **Notification**: Inform stakeholders of completion

### Running with Prefect

One-time execution:
```bash
python orchestration/batch_inference_flow.py
```

Scheduled deployment:
```bash
# Start Prefect server
prefect server start

# In another terminal, create deployment
python orchestration/deploy.py

# Start agent to execute scheduled flows
prefect agent start
```

### Customizing the Workflow

You can modify parameters in the `batch_inference_flow.py` script:

```python
batch_inference(
    year=2023,
    month=3,
    model_path="models/my_model.bin",
    output_file="custom_results.parquet",
    upload_to_cloud_storage=True,
    cloud_provider="gcs",  # or "s3", "azure"
    bucket_name="my-taxi-predictions"
)
```
