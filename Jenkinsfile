pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
            }
        }
        stage('Build') {
            steps {
                // Simulates compiling/running the application
                sh 'python3 app.py'
                // Wait for 15 seconds as instructed
                sleep 15
                // Ensures older builds are superseded by newer ones reaching this checkpoint
                milestone(1)
            }
        }
        stage('Send Notification') {
            steps {
                // Safe echo fallback workflow containing required env variables
                echo "Sending notification email to recipient@example.com..."
                echo "Subject: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}"
                echo "Body: Review your build details here: ${env.BUILD_URL}"
            }
        }
    }
}
