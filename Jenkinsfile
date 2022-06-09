pipeline {
    agent none
    stages {
        stage('Build') {
           
            steps {
                node('aws'){
                    git branch: 'rds_redis', 
                         url: "https://github.com/rrriii-dot/jenkins_nodejs_example.git"
                    withCredentials([usernamePassword(credentialsId:"docker-hub",usernameVariable:"username",passwordVariable:"pass")]){
                    sh 'docker build . -f dockerfile -t ${username}/jenkins_sprints:v1.0'
                    sh 'docker login -u ${username} -p ${pass}'
                    sh 'docker push ${username}/jenkins_sprints:v1.0'
                    }
                }
                // Get some code from a GitHub repository
                
            }
        }  
        stage ('deploy'){
            
            steps{
                node('private-ec2'){
                    git branch: 'rds_redis', 
                    withCredentials([usernamePassword(credentialsId:"docker-hub",usernameVariable:"username",passwordVariable:"pass")]){
                    sh 'docker login -u ${username} -p ${pass}'
                    sh 'docker pull ${username}/jenkins_sprints:v1.0'
                    sh 'docker run -p 3000:3000 -d ${username}/jenkins_sprints:v1.0'
                    }
                }
                
                
            }      
        }
    }
}
