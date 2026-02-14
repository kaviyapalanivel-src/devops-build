pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh './build.sh'
            }
        }

        stage('Deploy Container') {
            steps {
                sh './deploy.sh'
            }
        }
    }
}
