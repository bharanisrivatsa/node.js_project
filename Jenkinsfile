pipeline {
    agent any

    /* The tools block tells Jenkins to automatically add Node.js and npm to the PATH for this build */
    tools {
        // This name must match exactly what you configured in Manage Jenkins -> Tools
        nodejs 'nodejs' 
    }

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
                /* 'bat' is for Windows agents. If using Linux, change to 'sh' */
                bat 'npm install'
            }
        }

        stage('Start Application') {
            steps {
                echo 'Starting Node.js application...'
                /* WARNING: Running 'npm start' directly in a pipeline will cause 
                   the Jenkins build to hang indefinitely because it waits for the 
                   server process to end. 
                */
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