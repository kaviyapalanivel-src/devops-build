pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "kaviyapalaniveel/react-app"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'dev', url: 'https://github.com/kaviyapalanivel-src/devops-build.git'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    // Build the Docker image
                    def dockerImage = docker.build("${DOCKER_IMAGE}")
                    
                    // Push
