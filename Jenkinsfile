pipeline {
    agent any

parameters {
  choice choices: ['TEST', 'STAGE', 'DEV', 'QA', 'PROD'], name: 'ENV'
}

triggers {
        pollSCM('*/1 * * * *') // This sets up polling SCM to check for changes every minute
    }

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh ' /home/theshubhamgour/Documents/softwares/apache-maven-3.9.5/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                sh 'cp target/mexasoft.war /home/theshubhamgour/Documents/softwares/apache-tomcat-9.0.82/webapps ' 
            }
        }
    }
}

