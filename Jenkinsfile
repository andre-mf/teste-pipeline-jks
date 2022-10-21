pipeline {
    agent any

    stages{
        stage ('Build Docker Image') {
            steps{
                script {
                    dockerapp = docker.build("andremf/knews:${env.BUILD_ID}", "-f ./src/Dockerfile ./src")
                }
            }
        }
    }
}