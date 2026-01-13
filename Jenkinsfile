pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Pulling code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building project in progress'
                bat 'echo Build completed successfully!'
            }
        }

        stage('Validation Check') {
            steps {
                echo 'Validating project readiness'
                bat '''
                findstr READY=true check.txt > nul
                if errorlevel 1 (
                    echo Validation failed
                    exit 1
                ) else (
                    echo Validation passed
                )
                '''
            }
        }

        stage('Manager Approval') {
            steps {
                input message: 'Approve deployment?', ok: 'Approve'
            }
        }

        stage('Ready for Deployment') {
            steps {
                echo 'Deployment approved and ready'
            }
        }
    }
}
