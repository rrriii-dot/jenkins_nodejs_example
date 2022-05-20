pipeline {
    environment {
        registry = "amr158/nodejs"
        registryCredential = 'amr158'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Building our image') {
            steps{
                script {
                    dockerImage = docker.build registry
                    }
            }
        }
        stage('Deploy our image') {
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                    dockerImage.push()
                    }
                }
            }
        }
    }
}
