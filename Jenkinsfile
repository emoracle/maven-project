pipeline {
    agent any
    stages {
        stage('Build'){
            steps {
                bat "set m2_home=C:\Progs\apache-maven-3.6.0"
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
           build job: 'Deploy-to-staging'
           }
        }
    }
}