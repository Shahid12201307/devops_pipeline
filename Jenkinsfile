pipeline {
    agent any

    environment {
        IMAGE_NAME = 'book-recommender'
        CONTAINER_NAME = 'book-recommender-container'
        PORT = '5000'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Shahid12201307/devops_pipeline.git', branch: 'main'
            }
        }

        stage('Build Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Stop Container') {
            steps {
                bat '''
                    docker stop %CONTAINER_NAME% || exit 0
                    docker rm %CONTAINER_NAME% || exit 0
                '''
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d --name %CONTAINER_NAME% -p %PORT%:%PORT% %IMAGE_NAME%'
            }
        }
    }
}
