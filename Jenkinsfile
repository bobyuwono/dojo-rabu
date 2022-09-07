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
                DockerImage = docker.build("mailsyarief/nginx-dojo:latest")
            }
        }
        stage("Push Image"){
            steps{
                DockerImage.push()
            }
        }
        stage("Deploy Image"){
            steps{
                echo "4"
            }
        }
    }
}