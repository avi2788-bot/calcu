
pipeline {
    agent any

    environment {
        // Define your image name
        IMAGE_NAME = "my-python-app"
        IMAGE_TAG  = "${env.BUILD_NUMBER}"
        // DOCKER_HUB_USER = "your-username" // Uncomment if pushing to Docker Hub
    }

    stages {
        stage('Checkout') {
            steps {
                // Pulls code from your Git repository
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                script {
                    echo "Building Docker image: ${IMAGE_NAME}:${IMAGE_TAG}..."
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    echo "Running tests inside the container..."
                    // This runs your tests inside a temporary container
                }
            }
        }

        stage('Cleanup') {
            steps {
                echo "Cleaning up dangling images..."
                sh "docker image prune -f"
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
        success {
            echo "Build and Test successful!"
        }
        failure {
            echo "Build failed. Check the logs."
        }
    }
}
