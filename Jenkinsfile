pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
        IMAGE_NAME = 'ghazi838/app'
        IMAGE_TAG = "v${env.BUILD_NUMBER}"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push $IMAGE_NAME:$IMAGE_TAG'
            }
        }
    }
}This phase is where the "automation" in MLOps actually happens. You are going to link your GitHub repository to Jenkins, and write a script that tells Jenkins to automatically build and push your Docker image every time you update your code.
