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
                    dockerImage = docker.build("${DOCKER_IMAGE}")
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    // securely log in and push image using Jenkins credentials
                    withDockerRegistry(credentialsId: 'dockerhub_creds', url: 'https://index.docker.io/v1/') {
                        dockerImage.push()
                    }
                }
            }
        }

    }

    post {
        success {
            echo "Docker image ${DOCKER_IMAGE} pushed successfully!"
        }
        failure {
            echo "Pipeline failed. Check logs for details."
        }
    }
}
