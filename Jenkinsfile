pipeline {
    agent any

    tools {
        com.cloudbees.jenkins.plugins.customtools.CustomTool 'minikube' // Ensure the custom tool for Minikube is configured properly
        dockerTool 'docker' // Use the configured Docker tool
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Install dependencies using pip3
                    sh 'python3 -m pip install --upgrade pip'
                    sh 'python3 -m pip install pytest'
                    sh 'python3 -m pip install -r requirements.txt'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run Pytest tests
                    sh 'pytest tests/'
                }
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t data-analytics-app:latest -f deployment_app.dockerfile .'
                }
            }
        }
        stage('Deploy to Minikube') {
            steps {
                script {
                    // Point Docker to Minikube environment and build the image
                    sh 'eval $(minikube docker-env) && docker build -t data-analytics-app:latest .'
                    
                    // Apply Kubernetes manifests
                    sh 'kubectl apply -f k8s/deployment.yaml'
                    sh 'kubectl apply -f k8s/service.yaml'
                }
            }
        }
    }
}
