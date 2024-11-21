pipeline {
    agent any

    environment {
        GITHUB_CREDENTIALS = credentials('sasibharadwaja') // Replace with the ID you used
    }

    stages {
        stage('SCM Checkout') {
            steps {
                // Use GitHub credentials for checkout
                git credentialsId: 'sasibharadwaja', url: 'https://github.com/sasibharadwaja/my-web-app-ci.git'
            }
        }

        stage('Build docker image') {
            steps {
                // Build the Docker image
                sh 'docker build -t sasi630/nodeapp .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    // Login to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'sasi630-docker') {}
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    // Push the Docker image
                    docker.image('sasi630/nodeapp').push()
                }
            }
        }
    }
}
