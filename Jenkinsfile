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
                def DockerImage = docker.build("mailsyarief/nginx-dojo:latest")
                DockerImage.push()
            }
        }
        stage("Build Push") {
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