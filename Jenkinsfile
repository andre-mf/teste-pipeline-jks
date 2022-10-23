pipeline {
    agent any

    stages{
        stage ('Build Docker Image') {
            steps{
                sh 'docker ps -a'
                script {
                    dockerapp = docker.build("andremf/knews:${env.BUILD_ID}", "-f ./src/Dockerfile ./src")
                    // dockerapp = docker.build("andremf/knews:${env.BUILD_ID}", "-f kube-news/src/Dockerfile kube-news/src")
                }
            }
        }
    }
}