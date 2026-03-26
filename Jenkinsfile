pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Node.js dependencies...'
                bat 'npm install'
            }
        }

        stage('Start Application') {
            steps {
                echo 'Starting Node.js application...'
                bat 'npm start'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed'
        }
        success {
            echo 'Application started successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
