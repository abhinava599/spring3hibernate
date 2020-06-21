pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh script: 'mvn clean package'
                        }
                    }
               }
             }
              stage('Test-Result') {
            // Run the maven build
            junit 'target/surefire-reports/*.xml'
            }
