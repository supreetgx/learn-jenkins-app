pipeline {
    agent any

    stages {
        stage('Step 1: Dummy') {
            steps {
                sh '''
                echo 'Hello Supreet'
                echo `npm --version`
                '''
            }
        }
        stage('Step 2: Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo `npm --version`
                npm ci
                npm run build
                '''
            }
        }
        stage('Step 3: Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                npm test
                '''
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}