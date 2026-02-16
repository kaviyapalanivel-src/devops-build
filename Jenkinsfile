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

        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {

                        // If pushed to dev branch
                        if (env.BRANCH_NAME == 'dev') {
                            docker.image("${DOCKER_USER}/react-app")
                                .push("${DEV_REPO}")
                        }

                        // If merged to main branch (production)
                        if (env.BRANCH_NAME == 'main') {
                            docker.image("${DOCKER_USER}/react-app")
                                .push("${PROD_REPO}")
                        }

                    }
                }
            }
        }
    }
}

