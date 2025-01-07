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
            environment {
                NPM_CACHE_DIR = "${env.WORKSPACE}/.npm" // Set a writable npm cache directory
            }
            steps {
                script {
                    echo 'Starting Build Stage'
                }
                sh 'ls -la'
                sh 'node --version'
                sh 'npm --version'
                sh '''
                    mkdir -p $NPM_CACHE_DIR
                    npm config set cache $NPM_CACHE_DIR
                    npm ci
                '''
                sh 'ls -la'
            }
        }
    }
}
