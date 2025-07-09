pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vprichkapova/Student-Registry-App.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    bat 'npm install'
                }
            }
        }

        stage('Start Application') {
            steps {
                script {
                    bat 'start /b npm start'
                }
            }
        }

        stage('Wait for App to Start') {
            steps {
                script {
                    bat 'npx wait-on http://localhost:8080'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    bat 'npm test'
                }
            }
        }
    }

    post {
        always {
            echo "CI pipeline completed"
        }
    }
}