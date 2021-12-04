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
        stage('Deploy nginx in kubernets') {
            steps {
                sh 'kubectl apply -f . --kubeconfig /var/lib/jenkins/.kube/config'
            }
        }
    }
}
