pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('sasi630-docker')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/sasibharadwaja/my-web-app-ci.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t sasi630/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push sasi630/nodeapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
