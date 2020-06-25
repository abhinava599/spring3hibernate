pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh script: 'mvn clean package'
            }
        }
        stage ('deploy to tomcat')
        { 
           steps {
              sshagent(['tomcatdev']) {
                         sh 'scp -o StrictHostKeyChecking=no **/*.war vagrant@172.16.0.251:/opt/tomcat/webapps'
                         }
                 }
        }

    }
}
         
