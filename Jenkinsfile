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
                 sh "ssh -T 'root@172.31.47.120' /opt/apache/bin/./shutdown.sh"
                 sh "ssh -T 'root@172.31.47.120' rm -f /opt/apache/webapps/Spring3HibernateApp.war rm -fr /opt/tomcat/webapps/Spring3HibernateApp"
                 sh "scp target/Spring3HibernateApp.war 'deployer@172.31.47.120':/opt/tomcat/webapps/"
                 sh "ssh -T 'root@172.31.47.120' /opt/tomcat/bin/./startup.sh"
            }
        }

    }
}
         
