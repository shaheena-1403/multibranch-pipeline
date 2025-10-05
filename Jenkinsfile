pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t bankimage .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag bankimage shaheena1403/paytm:bank'
            }
        }
        stage ("push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh 'docker push shaheena1403/paytm:bank'
                   }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank -p 1111:80 shaheena1403/paytm:bank'
            }
        }
    }
}
