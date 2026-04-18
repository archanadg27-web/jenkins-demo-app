pipeline {

&#x20;   agent any



&#x20;   stages {

&#x20;       stage('Checkout') {

&#x20;           steps {

&#x20;               echo 'Code checked out successfully!'

&#x20;           }

&#x20;       }



&#x20;       stage('Install Dependencies') {

&#x20;           steps {

&#x20;               echo 'Installing dependencies using Docker...'

&#x20;               sh 'docker run --rm -v $WORKSPACE:/app -w /app node:18 npm install'

&#x20;           }

&#x20;       }



&#x20;       stage('Test') {

&#x20;           steps {

&#x20;               echo 'Running tests...'

&#x20;               sh 'docker run --rm -v $WORKSPACE:/app -w /app node:18 npm test'

&#x20;           }

&#x20;       }



&#x20;       stage('Build Docker Image') {

&#x20;           steps {

&#x20;               echo 'Building Docker image...'

&#x20;               sh 'docker build -t nodejs-jenkins-app:latest .'

&#x20;           }

&#x20;       }



&#x20;       stage('Deploy') {

&#x20;           steps {

&#x20;               echo 'Deploying application...'

&#x20;               sh '''

&#x20;                   docker stop nodejs-jenkins-app || true

&#x20;                   docker rm nodejs-jenkins-app || true

&#x20;                   docker run -d --name nodejs-jenkins-app -p 3000:3000 nodejs-jenkins-app:latest

&#x20;               '''

&#x20;           }

&#x20;       }

&#x20;   }



&#x20;   post {

&#x20;       success {

&#x20;           echo '✅ Pipeline completed successfully!'

&#x20;       }

&#x20;       failure {

&#x20;           echo '❌ Pipeline failed!'

&#x20;       }

&#x20;   }

}

