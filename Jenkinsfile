pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh "docker build -t nodejs_app ."
                sh "docker run --name nodejs_simple_app nodejs_app"
            }
        }
    }
}
