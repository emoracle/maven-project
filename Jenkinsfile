pipeline {
    agent any
    stages {
        stage('Deploy to Tomcat'){
           steps {
             timeout(time:5, unit:'DAYS'){
                 input message: "Keur deployment goed"
             }
             build job: 'Deploy-to-staging'
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