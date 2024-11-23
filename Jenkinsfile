pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Install dependencies
                    sh 'pip install -r requirements.txt'
                }
            }
        }
        stage('Test') {
            steps {
                // Run Pytest tests
                sh 'pytest'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    // Build the Docker image
                    docker.build('my-python-app:latest')
                }
            }
        }
        stage('Deploy to Minikube') {
            steps {
                script {
                    // Load Docker image to Minikube
                    sh 'eval $(minikube docker-env) && docker build -t my-python-app:latest .'
                    
                    // Apply Kubernetes deployment files
                    sh 'kubectl apply -f k8s-deployment.yaml'
                }
            }
        }
    }
}
