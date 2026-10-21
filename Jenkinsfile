pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/S-Vinay121/ccd-docker.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t cloud-app .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                    which minikube && minikube image load cloud-app:latest || true
                    kubectl apply -f k8s-deployment.yaml
                    kubectl rollout restart deployment/cloud-app-deployment
                '''
            }
        }
    }
}

