pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t busimage .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag busimage shaheena1403/paytm:bus'
            }
        }
        stage ("push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh 'docker push shaheena1403/paytm:bus'
                   }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus -p 2222:80 shaheena1403/paytm:bus'
            }
        }
    }
}
