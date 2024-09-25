pipeline {
    agent any

    environment {
        // Set npm cache directory to a writable path
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm" 
    }

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
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
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm run test
                    ls -la
                    if [ -e /builds/index.html]
                        then
                            echo "File index.htlm exists."
                    else 
                        echo "There's no such a file."
                    fi
                '''
            }  
    }
}
