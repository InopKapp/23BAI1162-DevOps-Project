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
                bat "docker build -t corporate-website:${env.BUILD_NUMBER} ."
            }
        }
        
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s/deployment.yaml'
                bat 'kubectl apply -f k8s/service.yaml'
                bat "kubectl set image deployment/corporate-website-deployment corporate-website=corporate-website:${env.BUILD_NUMBER}"
                bat 'kubectl rollout restart deployment/corporate-website-deployment'
            }
        }
    }
}
