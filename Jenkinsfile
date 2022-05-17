pipeline {
    agent any

    stages {
        stage ('unit test') {
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-key') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube --status'
                    }    
                }  
            }
        }
    }
}