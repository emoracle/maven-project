pipeline {
    agent any

    tools {
        maven 'localMaven'
    }

    stages {
         stage('Build'){
            steps {
                bat "mvn clean package"
            }
            post {
                success {
                   echo "archiving"
                   archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to Tomcat'){
           steps {
             timeout(time:5, unit:'DAYS'){
                 input message: "Keur deployment goed"
             }
             build job: 'deploy-to-staging'
           }
           post {
               success {
                   echo "Deployed naar productie"
               }

               failure {
                   echo "Deployment mislukt"
               }
           }
        }
    }
}