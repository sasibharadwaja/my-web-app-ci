pipeline {
    agent any

    environment {
        GITHUB_CREDENTIALS = credentials('sasibharadwaja') 
    }

    stages {
        stage('SCM Checkout') {
            steps {
                git credentialsId: 'sasibharadwaja', url: 'https://github.com/sasibharadwaja/my-web-app-ci.git'
            }
        }

    stage('Debug') {
        steps {
            echo "Successfully checked out repository"
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
                    docker.withRegistry('https://registry.hub.docker.com', 'sasi630') {}
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
