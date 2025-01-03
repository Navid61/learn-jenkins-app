pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
           
                    sh 'npm cache clean --force'
                    sh 'npm ci'
                    // Optional cleanup step to ensure a clean workspace before build
                    sh 'rm -rf node_modules' // Only if needed to ensure a clean state

                    // Display the current directory and Node.js versions
                    sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                    '''
               
            }
        }
    }
}