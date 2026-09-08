pipeline {
    agent any

    stages {
        stage('Step 1') {
            steps {
                sh '''
                echo 'Hello Supreet'
                echo `npm --version`
                '''
            }
        }
        stage('Step 2') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                echo 'Hello Goswami'
                echo `npm --version`
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