pipeline {
    agent none

    stages {
        stage('w/o docker') {
            agent any
            steps {
                sh 'echo "Without docker"'
                sh 'whoami'
                sh 'sudo docker images'
            }
        }

        stage('w/ docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh 'echo "With docker"'
                sh 'npm --version'
            }
        }
    }
}