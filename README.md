
# Data Analytics Application

This repository contains a Python-based data analytics application that is packaged into a Docker container and deployed using Kubernetes, Minikube, and Jenkins. The project includes an automated CI/CD pipeline to streamline the processes of building, testing, and deploying the application.

## Table of Contents
- Overview
- Technologies Used
- Project Structure
- Setup Instructions
  1. Clone the Repository
  2. Set Up Python Environment
  3. Run the Application Locally
- Containerization with Docker
- CI/CD Pipeline with Jenkins
- Kubernetes Deployment with Minikube
- Testing
- Author

## Overview

This project showcases how to:
- Build a Python-based data analytics application.
- Containerize the application using Docker.
- Automate build, test, and deployment workflows with Jenkins.
- Deploy the application to a local Kubernetes cluster powered by Minikube.
- Perform automated testing with Pytest.

## Technologies Used
- **Version Control**: GitHub
- **Programming Language**: Python
- **Containerization**: Docker
- **CI/CD Tool**: Jenkins
- **Orchestration**: Minikube (Kubernetes)
- **Testing Framework**: Pytest

## Project Structure

```
├── data                   # Contains sample data files
│   └── sample.csv         # Example CSV data for the application
├── src                    # Application source code
│   ├── app.py             # Flask-based web application
│   ├── analysis.py        # Data processing logic
│   └── utils.py           # Helper functions
├── tests                  # Unit test files
│   └── test_analysis.py   # Pytest tests for analysis
├── k8s                    # Kubernetes configuration files
│   ├── deployment.yaml    # Kubernetes deployment config
│   └── service.yaml       # Kubernetes service config
├── Dockerfile             # Dockerfile for containerizing the app
├── requirements.txt       # Python project dependencies
├── Jenkinsfile            # Jenkins pipeline definition
└── README.md              # Project documentation
```

## Setup Instructions

### 1. Clone the Repository
To get started, clone the repository to your local machine:
```bash
git clone https://github.com/sameersharmaAI/data-analytics-app.git
cd data-analytics-app
```

### 2. Set Up Python Environment
Create a virtual environment and activate it:
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

Install the necessary dependencies:
```bash
pip install -r requirements.txt
```

### 3. Run the Application Locally
Start the Flask application:
```bash
python src/app.py
```

Now you can access the application by visiting [http://127.0.0.1:5000](http://127.0.0.1:5000) in your browser.

## Containerization with Docker

### Build the Docker Image
To containerize the application, run the following command:
```bash
docker build -t data-analytics-app .
```

### Run the Docker Container
Once the image is built, run the container:
```bash
docker run -p 5000:5000 data-analytics-app
```

## CI/CD Pipeline with Jenkins

### Set Up Jenkins
1. Install Jenkins on your local machine.
2. Install the required plugins, such as Docker and GitHub.

### Define the Pipeline
The provided `Jenkinsfile` defines the build, test, and deploy stages. You can modify it based on your needs.

### Run the Pipeline
In Jenkins, configure a new pipeline job pointing to this GitHub repository and trigger the pipeline to automate the process.

## Kubernetes Deployment with Minikube

### Start Minikube
To start the Minikube local cluster, run:
```bash
minikube start
```

### Deploy the Application to Kubernetes
Apply the Kubernetes manifests to deploy the app:
```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

### Access the Application
Retrieve the Minikube IP to access the application:
```bash
minikube ip
```
Visit the provided IP in your browser.

## Testing

To run the unit tests using Pytest, execute the following:
```bash
pytest tests/
```

Ensure all tests pass successfully.

## Author

**Sameer Sharma**  
GitHub: [sameersharmaAI](https://github.com/sameersharmaAI)  
