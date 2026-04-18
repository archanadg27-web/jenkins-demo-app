pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Stage 1: Code checked out!'
            }
        }

        stage('Test') {
            steps {
                echo 'Stage 2: Tests passed!'
            }
        }

        stage('Build') {
            steps {
                echo 'Stage 3: Build complete!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Stage 4: Deployed successfully!'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
