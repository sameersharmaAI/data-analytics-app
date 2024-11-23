pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Install dependencies with pip3
                    sh 'python3 -m pip install --upgrade pip'
                    sh 'python3 -m pip install -r requirements.txt'
                }
            }
        }
        stage('Test') {
            steps {
                // Run Pytest tests
                sh 'pytest tests/'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.build('my-python-app:latest')
                }
            }
        }
        stage('Deploy to Minikube') {
            steps {
                script {
                    sh 'eval $(minikube docker-env) && docker build -t my-python-app:latest .'
                    sh 'kubectl apply -f k8s-deployment.yaml'
                }
            }
        }
    }
}
