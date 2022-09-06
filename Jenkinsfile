def DockerImage
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
                script {
                    DockerImage = docker.build("mailsyarief/nginx-dojo:latest")
                }
            }
        }
        stage("Push Image") {
            steps {
                script {
                    DockerImage.push()
                }
            }
        }
        stage("Deploy Image") {
            steps {
                sshCommand remote: remote, command: "docker run -p 80:80 -d --name dojo_nginx mailsyarief/nginx-dojo:latest"
            }
        }
    }
}