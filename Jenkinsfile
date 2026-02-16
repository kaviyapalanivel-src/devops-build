pipeline {
    agent any

    environment {
        DOCKER_USER = "kaviyapalaniveel"
        DEV_REPO = "dev"
        PROD_REPO = "prod"
    }

    stages {

        stage('Build Image') {
            steps {
                script {
                    docker.build("${DOCKER_USER}/react-app")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-creds') {

                        if (env.BRANCH_NAME == 'dev') {
                            docker.image("${DOCKER_USER}/react-app")
                                .push("${DEV_REPO}")
                        }

                        if (env.BRANCH_NAME == 'master') {
                            docker.image("${DOCKER_USER}/react-app")
                                .push("${PROD_REPO}")
                        }

                    }
                }
            }
        }
    }
}

