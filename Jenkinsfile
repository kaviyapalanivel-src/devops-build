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
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Image') {
            steps {
                withDockerRegistry(credentialsId: 'dockerhub_creds') {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }

    }
}
