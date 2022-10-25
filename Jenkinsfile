pipeline {
    agent any

//     stages{
//         stage ('Build Docker Image') {
//             steps{
//                 sh 'docker ps -a'
//                 script {
//                     dockerapp = docker.build("andremf/knews:${env.BUILD_ID}", "-f ./src/Dockerfile ./src")
//                 }
//             }
//         }
//
//         stage ('Push Docker Image') {
//             steps {
//                 script {
//                     docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
//                         dockerapp.push('latest')
//                         dockerapp.push("${env.BUILD_ID}")
//                     }
//                 }
//             }
//         }

        stage('Apply Kubernetes files') {
            environment {
                tag_version = "${env.BUILD_ID}"
            }
            steps {
                script {
                    withKubeConfig([credentialsId: 'kubeconfig', serverUrl: 'https://200.96.230.83:36047']) {
                        sh 'sed -i "s/{{TAG}}/$tag_version/g" ./k8s/deployment.yaml'
                        sh 'kubectl apply -f ./k8s/deployment.yaml'
                    }
                }
            }
        }
    }
}