pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t adinarayana25/myrepo:bus .'
            }
        }
         stage('Push') {
            steps {
               script{
                   withDockerRegistry(credentialsId: 'docker-credientials', url: 'https://github.com/adiduggempudi/multibranch-pipeline.git') {
                              sh 'docker push adinarayana25/myrepo:bus'
                       }
               }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus -p 8888:80 shaikmustafa/abinay:bus'
            }
        }
    }
}
