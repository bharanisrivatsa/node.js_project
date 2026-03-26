pipeline {
    agent any

    tools {
        // Ensure this matches your 'Global Tool Configuration' name
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
                bat 'npm install'
            }
        }

        stage('Start Application') {
            steps {
                echo 'Starting Node.js application in the background...'
                /* 1. 'set BUILD_ID=dontKillMe' prevents Jenkins from killing the process when the job ends.
                   2. 'start /B' runs the command in the background without opening a new window.
                */
                bat 'set BUILD_ID=dontKillMe && start /B npm start'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed'
        }
        success {
            echo 'Application background process initiated successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
