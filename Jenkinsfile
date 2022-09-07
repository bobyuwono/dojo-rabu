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
                echo "2"
            }
        }
        stage("Push Image"){
            steps{
                echo "3"
            }
        }
        stage("Deploy Image"){
            steps{
                echo "4"
            }
        }
    }
}