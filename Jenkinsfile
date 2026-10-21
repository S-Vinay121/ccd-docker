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

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f cloud-app || true
                    docker run -d --name cloud-app -p 5000:80 cloud-app
                '''
            }
        }
    }
}

