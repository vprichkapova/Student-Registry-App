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
    checkout scm

}

stage ('Install Dependencies'){
    steps {

script {

    if(isUnix()) {
        sh 'npm install'
    } else {
        sh 'npm install'
    }
}
stage ("Start Application and run tests") {

steps {
    script {
        sh "npm start &"
        sh "wait-on http://localhost:8080"
        sh "npm test"
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