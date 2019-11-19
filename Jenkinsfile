pipeline {
    agent { any }
    stages {
        stage('Checkout scm') {
            steps {
                checkout scm
            }
        }
        stage('Deploy') {
            steps {
                withDockerContainer([image: 'buoyantio/kubectl:latest']) {
                    withKubeConfig([credentialsId: 'kube-admin', serverUrl: 'https://test.com']) {
                        sh 'kubectl --help'
                    }
                }
            }
        }
    }
}