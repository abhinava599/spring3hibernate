pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh script: 'mvn clean package'
            }
        }
        stage('Deploy Tomcat') {
            steps {
                 sh "ssh -T 'deployer@http://172.16.0.251' /opt/apache/bin/./shutdown.sh"
                 sh "ssh -T 'deployer@http://172.16.0.251' rm -f /opt/apache/webapps/Spring3HibernateApp.war rm -fr /opt/tomcat/webapps/Spring3HibernateApp"
                 sh "scp target/Spring3HibernateApp.war 'deployer@http://172.16.0.251':/opt/tomcat/webapps/"
                 sh "ssh -T 'deployer@http://172.16.0.251' /opt/tomcat/bin/./startup.sh"
            }
        }

    }
}
         
