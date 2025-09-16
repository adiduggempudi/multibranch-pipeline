pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t image5 .'
            }
        }
        stage('Tag'){
            steps{
                sh 'docker tag image5 adinarayana25/myrepo:train '
            }
        }
         stage('Push') {
            steps {
               script{
                   withDockerRegistry(credentialsId: 'docker-credientials', url: 'https://github.com/adiduggempudi/multibranch-pipeline.git') {
                              sh 'docker push adinarayana25/myrepo:train'
                       }
               }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 9999:80 shaikmustafa/abinay:train'
            }
        }
    }
}
