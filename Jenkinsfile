pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh './build.sh'
            }
        }

        stage('Push Image') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'dev') {
                        sh 'docker tag react-app:latest kaviyapalaniveel/dev:latest'
                        sh 'docker push kaviyapalaniveel/dev:latest'
                    }
                    else if (env.BRANCH_NAME == 'main') {
                        sh 'docker tag react-app:latest kaviyapalaniveel/prod:latest'
                        sh 'docker push kaviyapalaniveel/prod:latest'
                    }
                }
            }
        }

        stage('Deploy Container') {
            steps {
                sh './deploy.sh'
            }
        }
    }
}

