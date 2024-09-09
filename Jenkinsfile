pipeline {
    agent any

        stage('w/ docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'echo "With docker"'
                sh 'npm --version'
                sh 'npm ci'
                sh 'npm run build'
                sh 'touch 123.txt'
                sh 'echo test > 123.txt'
            }
        }
    post {
        success {
            archiveArtifacts artifacts: '123.txt'
        }
    }
}
