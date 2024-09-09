pipeline {
    agent any

    stages {
        stage('w/o docker') {
            steps {
                sh 'echo "Without docker"'
                sh 'whoami'
                sh 'docker images'
            }
        }

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
                sh 'touch 123.txt'
                sh 'echo test > 123.txt'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: '123.txt'
        }
    }
}