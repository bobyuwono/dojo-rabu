def DockerImage

pipeline {
    agent any //job ini bakal jalan dimana?
    stages {
        stage("Docker Login"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhub-mailsyarief',usernameVariable: 'USERNAME',passwordVariable: 'PASSWORD')]) {
                    sh 'docker login --username $USERNAME --password $PASSWORD'
                }
            }
        }
        stage("Build Docker Image"){
            steps{
                script {
                    DockerImage = docker.build("mailsyarief/nginx-dojo:latest")
                }
            }
        }
        stage("Push Image"){
            steps{
                script {
                    DockerImage.push()
                }
            }
        }
        stage("Deploy Image"){
            steps{
                sh 'ssh -t jenkins@34.122.123.221 "docker run -p 80:80 -d --name dojo_nginx mailsyarief/nginx-dojo:latest" '
            }
        }
    }
}