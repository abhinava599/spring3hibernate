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
              stage('DeployToStaging') {
            when {
                branch 'master'
            }
            steps {
                withCredentials([usernamePassword(credentialsId: 'webserver', usernameVariable: 'Username', passwordVariable: 'Password')]) {
                    sshPublishe
                        failOnError: true,
                        continueOnError: false,
                        publishers: [
                            sshPublisherDesc(
                                configName: 'staging',
                                sshCredentials: [
                                    username: "$Username",
                                    encryptedPassphrase: "$Password"
                                ], 
                                transfers: [
                                    sshTransfer(
                                        sourceFiles: '**/*.war',
                                        remoteDirectory: '/Weabapps',
                                        execCommand: 'sudo /usr/bin/systemctl stop train-schedule && rm -rf /opt/train-schedule/* && unzip /tmp/trainSchedule.zip -d /opt/train-schedule && sudo /usr/bin/systemctl start train-schedule'
                                    )
                                ]
                            )
                        ]
                    )
                }
            }
        }
