pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t trainimage .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag trainimage shaheena1403/paytm:train'
            }
        }
        stage ("push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh 'docker push shaheena1403/paytm:train'
                   }
                }
            }
        }

        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 3333:80 shaheena1403/paytm:train'
            }
        }
    }
}
