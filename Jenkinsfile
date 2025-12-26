pipeline {
    agent any

    stages {

        stage('Start') {
            steps {
                echo 'Starting Jenkins pipeline for Docker project'
            }
        }

        stage('Clone Code') {
            steps {
                git url: 'https://github.com/Kartik71845/Docker-Portfolio.git', branch: 'main'
                echo 'Code cloned from GitHub repository'
            }
        }

        stage('Build and Run') {
            steps {
                sh '''
                echo "Workspace content:"
                ls -la

                docker-compose down || true
                docker-compose up -d --build
                '''
                echo 'Docker containers built and running'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
