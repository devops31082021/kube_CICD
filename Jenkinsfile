properties([pipelineTriggers([githubPush()])])
pipeline {
    agent any
    stages {
        stage('Build docker image with docker file') {
            steps {
                sh """
                docker build -t nginx:test .
                docker tag nginx:test devops31082021/nginx-test
                """
            }
        }
        
        stage('Push docker image to  docker hub') {
            steps {
                sh """
                docker login -u devops31082021 -p devops31082021
                docker push devops31082021/nginx-test
                """
            }
        }
        stage('Deploy nginx in kubernets') {
            steps {
                sh '''
                kubectl delete deploy nginx --kubeconfig /var/lib/jenkins/.kube/config
                kubectl apply -f . --kubeconfig /var/lib/jenkins/.kube/config
                '''
            }
        }
    }
}
