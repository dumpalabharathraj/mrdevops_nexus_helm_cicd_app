pipeline{
    agent any
    stages{
        stage('sonar quality status'){
            agent{
                docker{
                    image 'maven'

                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {

                     sh 'mvn clean package sonar:sonar'   
                    
                 }
                }
            }
        }
        
        stage('Docker build & docker push to nexus repo'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'Nexus', variable: 'nexus_creds')]) {
                    sh '''
                     docker build -t 23.23.37.129:8083
                     '''
                    }

                }
            }
        }
    }
}
