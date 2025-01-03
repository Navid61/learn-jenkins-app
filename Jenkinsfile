pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:20-alpine'
                    reuseNode true
                }
            }
            steps {
                script {
                    echo 'Starting Build Stage'
                }
                sh 'ls -la'
                sh 'node --version'
                sh 'npm --version'
                sh 'rm -rf node_modules'
                sh 'npm cache clean --force'
                sh 'npm install'
                sh 'ls -la'
            }
        }
    }
}
