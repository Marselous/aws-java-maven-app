#!/usr/bin.env groovy

pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application..."

                }
            }
        }
        stage("build") {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    def dockerCmd = "docker run -d -p 3080:3080 --name java-app justfreak/demo-app:1.1.4-19"
                    sshagent(['ssh-srv5-key']) {
                        sh "ssh -o StrictHostKeyChecking=no zerg@192.168.56.108 ${dockerCmd}"
                    }
                }
            }
        }               
    }
} 
