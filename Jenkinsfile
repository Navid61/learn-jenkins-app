pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u 1000:1000' // Run as a non-root user
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
                sh 'npm ci'
                sh 'ls -la'
            }
        }
    }
}
