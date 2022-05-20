pipeline {
    agent any
    stages {
        stage('Building our image') {
            steps{
                sh 'docker build -t amr158/nodejs .'
            }
        }
    }
}
