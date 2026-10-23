pipeline
    { agent
    any

    stages {
        stage('Checkout')
        { steps {
            checkout scm
        }
        }

        stage('Test')
        { steps {
            sh 'test -f index.html'
            echo 'HTML file exists - Test passed'
        }
        }

        stage('Build')
        { steps {
            echo 'Preparing HTML application...'
            sh 'mkdir -p build'
            sh 'cp index.html build'
        }
        }

        stage('Deploy')
        { steps {
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
