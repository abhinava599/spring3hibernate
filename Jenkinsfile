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
                          sh "ssh -T 'vagrant@172.16.0.251' /opt/tomcat/bin/./shutdown.sh"
						  sh "ssh -T 'vagrant@172.16.0.251' rm -f /opt/tomcat/webapps/petclinic.war rm -fr /opt/tomcat/webapps/Spring3HibernateApp"
                          sh "scp target/Spring3HibernateApp.war 'vagrant@172.16.0.251':/opt/tomcat/webapps/"
						  sh "ssh -T 'vagrant@172.16.0.251' /opt/tomcat/bin/./startup.sh"
                         }
                 }
        }

    }
}
         


