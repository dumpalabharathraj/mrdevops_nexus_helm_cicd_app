pipeline{
    agent any
    tools{
        maven 'Maven3'
    stages{
        stage('Checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/dumpalabharathraj/demo-counter-app.git']])
        stage('sonar quality check'){
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
        
            }
        }
        
            
        }
    }
}
