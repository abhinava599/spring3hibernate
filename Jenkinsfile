pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh script: 'mvn clean package'
            }
        }
        stage('Stop Tomcat') {
                sh "ssh -T 'vagrant@172.16.0.251' /opt/tomcat/bin/./shutdown.sh"
                }
        
                stage('War File Deployment') {
                sh "ssh -T 'vagrant@172.16.0.251' rm -f /opt/tomcat/webapps/petclinic.war rm -fr /opt/tomcat/webapps/Spring3HibernateApp"
                sh "scp target/Spring3HibernateApp.war 'vagrant@172.16.0.251':/opt/tomcat/webapps/"
                }
                stage('Start Tomcat') {
                sh "ssh -T 'vagrant@172.16.0.251' /opt/tomcat/bin/./startup.sh"
                }

    }
}
         


