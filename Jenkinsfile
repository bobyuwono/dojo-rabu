pipeline {
    agent any
    stages {
        stage("Docker Login") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-mailsyarief', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'docker login --username $USERNAME --password $PASSWORD'
                }                
            }
        }
        stage("Build Image") {
            steps {
                echo "test"
            }
        }
        stage("Deploy Image") {
            steps {
                echo "deploy nginx"
            }
        }
    }
}