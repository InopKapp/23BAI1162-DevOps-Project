pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Maven Build') {
            steps {
                // Using 'bat' because Jenkins is running on Windows
                bat 'mvn clean package'
            }
        }
        
        stage('Docker Build') {
            steps {
                bat 'docker build -t corporate-website:v1 .'
            }
        }
        
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s/deployment.yaml'
                bat 'kubectl apply -f k8s/service.yaml'
                // This ensures Kubernetes fetches the newest version of the image
                bat 'kubectl rollout restart deployment/corporate-website-deployment'
            }
        }
    }
}
