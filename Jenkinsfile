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

        stage('Start Application and run tests') {
            steps {
                script {
                    bat "start /b npm start"
                    bat "wait-on http://localhost:8080"
                    bat "npm test"
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
