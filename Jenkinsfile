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
                    bat 'start /b npm start'
                }
            }
        }
    }
        stage('Run tests') {
            steps {
                script {
                    bat 'start npm test'
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
