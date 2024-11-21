pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('sasi630-docker')
    }

    stages {
        stage('SCM Checkout') {
            steps {
                git 'https://github.com/sasibharadwaja/nodeapp.git'
            }
        }

        stage('Build docker image') {
            steps {
                sh 'docker build -t sasi630/nodeapp .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'sasi630-docker') {
                    }
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    docker.image('sasi630/nodeapp').push()
                }
            }
        }
    }
}
