pipeline {
    agent any

    environment {
        IMAGE_NAME = "readtext/hello-app"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/naresh041/test-auto-docker-deployment.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop hello-container || true
                docker rm hello-container || true
                docker run -d -p 3001:3001 --name hello-container $IMAGE_NAME
                '''
            }
        }
    }
}
