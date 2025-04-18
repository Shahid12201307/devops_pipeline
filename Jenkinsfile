pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/Shahid12201307/devops_pipeline.git'
            }
        }
        stage('Build Docker image') {
            steps {
                script {
                    docker.build('book-recommender')
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    docker.image('book-recommender').run('-p 5000:5000')
                }
            }
        }
    }
}
