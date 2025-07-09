pipeline {

agent any

environment  {

    NODE_VERSIONS = '22.x'
}

tools {

    nodejs "${NODE_VERSIONS}"
}
stages {

stage('Checkout'){

steps {
    git branch: 'main',
        url: 'https://github.com/vprichkapova/Student-Registry-App.git'

}

stage ('Install Dependencies'){
    steps {

script {
        bat 'npm install'   
}
stage ("Start Application and run tests") {

steps {
    script {
        bat "npm start &"
        bat "wait-on http://localhost:8080"
        bat "npm test"
    }
}
}
    post {
        always {
             echo "CI pipeline completed"
        }
    }
}
}