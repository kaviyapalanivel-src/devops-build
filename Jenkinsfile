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

        stage('Build and Push Image') {
            steps {
                script {
                    // Build Docker image
                    def dockerImage = docker.build("${DOCKER_IMAGE}")
                    
                    // Push to Docker Hub using credentials
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
