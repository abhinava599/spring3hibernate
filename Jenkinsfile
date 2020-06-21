pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh script: 'mvn clean package'
                        }
                    }
  
          stage('Testing Stage') {
                steps {
                     sh script: 'mvn test'
                        }
                                   }
        }
}
