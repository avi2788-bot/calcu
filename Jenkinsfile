pipeline {
    agent any

    environment {
        IMAGE_NAME = "calculator-app-test"
    }

    stages {
        stage('Build Image') {
            steps {
                script {
                    // בניית ה-Image מתוך התיקייה הפנימית
                    sh "docker build -t ${IMAGE_NAME} ./calculator-app"
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // הרצת הבדיקות בתוך הקונטיינר
                    // --rm דואג למחוק את הקונטיינר בסיום ההרצה
                    sh "docker run --rm ${IMAGE_NAME} pytest tests/"
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    // ניקוי ה-Image המקומי כדי לא להעמיס על השרת
                    sh "docker rmi ${IMAGE_NAME}"
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        failure {
            echo 'Tests failed! Check the logs.'
        }
    }
}
