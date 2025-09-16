pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage('Tag'){
            steps{
                sh 'docker tag image3 adinarayana25/myrepo:bank '
            }
        }
         stage('Push') {
            steps {
               script{
                   withDockerRegistry(credentialsId: 'dockerhub-credientials') {
                         sh 'docker push adinarayana25/myrepo:bank '
                       }
               }
            }
        }
        stage ('Deploy') {
            steps {
                sh 'docker run -itd --name bank2 -p 4455:80 adinarayana25/myrepo:bank'
            }
        }
    }
}
