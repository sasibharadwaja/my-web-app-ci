pipeline {
    agent any

    environment {
        // Optional: Define environment variables (if needed)
        GIT_URL = 'https://github.com/sasibharadwaja/my-web-app-ci.git'
        BRANCH_NAME = 'master'  // Replace with your branch name
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Explicitly clone the Git repository
                    git url: https://github.com/sasibharadwaja/my-web-app-ci.git, branch: master
                }
            }
        }

        stage('Build') {
            steps {
                // Install dependencies or perform build steps
                script {
                    // For example, install Node.js dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Test') {
            steps {
                // Add testing steps here
                script {
                    // Example: Run tests
                    sh 'npm test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deployment steps (e.g., Docker, server deployment, etc.)
                script {
                    // Example deploy step
                    echo 'Deploying application'
                }
            }
        }

        stage('Clean Up') {
            steps {
                // Optionally clean up workspace (e.g., remove temporary files)
                deleteDir() // Cleans the workspace at the end of the pipeline
            }
        }
    }

    post {
        success {
            // Optional: actions after successful build (e.g., send notifications)
            echo 'Build completed successfully.'
        }
        failure {
            // Optional: actions after failed build (e.g., send error notifications)
            echo 'Build failed.'
        }
        always {
            // Clean up or perform tasks that should happen no matter what
            echo 'Cleaning up resources.'
        }
    }
}
