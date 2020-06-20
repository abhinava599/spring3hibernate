pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh script: 'mvn clean package'
                archiveArtifacts artifacts: 'dist/spring3hibernate.war'
            }
        }
    }
}
