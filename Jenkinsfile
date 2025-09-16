pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 shaikmustafa/paytm:bank'
            }
        }
        stage('Push') {
            steps {
                script {
                   withDockerRegistry(url: 'https://app.docker.com/accounts/ravalikn') {
                        sh 'docker push shaikmustafa/paytm:bank'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 shaikmustafa/paytm:bank'
            }
        }
    }
}
