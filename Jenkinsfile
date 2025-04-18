pipeline {
    agent any

    environment {
        IMAGE_NAME = 'book-recommender'
        CONTAINER_NAME = 'book-recommender-container'
        PORT = '5000'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/Shahid12201307/devops_pipeline.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "🔨 Building Docker image..."
                    sh "docker build -t ${IMAGE_NAME} ."
                }
            }
        }

        stage('Stop Existing Container') {
            steps {
                script {
                    echo "🛑 Stopping existing container if running..."
                    sh """
                        docker stop ${CONTAINER_NAME} || true
                        docker rm ${CONTAINER_NAME} || true
                    """
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo "🚀 Running container..."
                    sh "docker run -d --name ${CONTAINER_NAME} -p ${PORT}:${PORT} ${IMAGE_NAME}"
                }
            }
        }
    }
}
