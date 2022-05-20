pipeline {
    agent any
    stages {
        stage('Building our image') {
            steps{
                sh 'docker build -t nodejs-app .'
            }
        }
        stage('run image') {
            steps{
                sh 'docker run --name nodejs-app nodejs-app'
            }
        }
    }
}
