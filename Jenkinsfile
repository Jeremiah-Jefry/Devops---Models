pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'test -f index.html'
                    } else {
                        bat 'if exist index.html (echo HTML file exists - Test passed) else (exit /b 1)'
                    }
                }
                echo 'HTML file exists - Test passed'
            }
        }

        stage('Build') {
            steps {
                echo 'Preparing HTML application...'
                script {
                    if (isUnix()) {
                        sh 'mkdir -p build && cp index.html build/'
                    } else {
                        bat 'if not exist build mkdir build && copy /Y index.html build\\'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying HTML application...'
                echo 'HTML application deployed successfully!'
            }
        }
    }

    post {
        success {
            echo 'HTML application deployed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
