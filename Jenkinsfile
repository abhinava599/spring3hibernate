pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh script: 'mvn clean package'
                archiveArtifacts artifacts: 'target/Spring3Hibernate.war'
            }
        }
    }
}
