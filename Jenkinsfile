pipeline {
    agent any

    environment {
        APP_NAME = "jenkins-demo"
        VERSION = "1.0"
    }

    stages {

        stage('Build') {
            steps {
                sh 'echo "Building $APP_NAME version $VERSION..."'
                sh 'node app.js'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                sh 'echo "All tests passed!"'
            }
        }

        stage('Deploy to Staging') {
            steps {
                sh 'echo "Deploying to staging server..."'
            }
        }

        stage('Deploy to Production') {
            when {
                expression { env.GIT_BRANCH == 'origin/main' }
            }
            steps {
                sh 'echo "Deploying to production server..."'
            }
        }

    }

    post {
        success {
            echo "Pipeline passed! App is live."
        }
        failure {
            echo "Pipeline failed! Check the logs."
        }
        always {
            echo "Pipeline finished."
        }
    }
}
