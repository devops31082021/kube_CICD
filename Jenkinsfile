properties([pipelineTriggers([githubPush()])])
pipeline {
    agent any
    stages {
        stage('Deploy nginx in kubernets') {
            steps {
                sh 'kubectl apply -f .'
            }
        }
    }
}
