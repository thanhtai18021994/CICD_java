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
                sh 'echo hello'
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-key') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube \
                            -Dsonar.projectKey=sonarserver \
                    }    
                }  
            }
        }
    }
}