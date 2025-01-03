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
                    // Display the current directory and Node.js versions
                    sh '''
                    ls -la
                    node --version
                    npm --version
                    rm -rf node_modules
                    npm cache clean --force
                    npm install
                    npm ci
                    npm run build
                    ls -la
                    '''
               
            }
        }
    }
}