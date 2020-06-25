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
                         sh 'vagrant@172.16.0.251:/opt/tomcat/bin/./shutdown.sh'
                         sh 'vagrant@172.16.0.251: rm -f /opt/tomcat/webapps/Spring3HibernateApp.war rm -fr /opt/tomcat/webapps/Spring3HibernateApp'
                         sh 'scp -o StrictHostKeyChecking=no **/*.war vagrant@172.16.0.251:/opt/tomcat/webapps'
                         sh 'vagrant@172.16.0.251:/opt/tomcat/bin/./startup.sh'
                         }
                 }
        }

    }
}
