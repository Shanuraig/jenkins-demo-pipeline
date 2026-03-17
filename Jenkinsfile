pipeline {
    agent any

    triggers {
        // Use ONE of these:
        // 1) Webhook (recommended): add GitHub webhook (no cron needed here)
        // OR
        // 2) Poll SCM fallback: uncomment to poll every minute
        // pollSCM('* * * * *')
    }

    options {
        timestamps()
        disableConcurrentBuilds()
    }

    stages {
        stage('Checkout') {
            steps {
                // Jenkins automatically checks out with the right SCM config if tied to a Multibranch or Pipeline job with SCM set
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'echo "Hello from Jenkins build"'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "Pretend tests passed ✅"'
            }
        }
    }

    post {
        success { echo 'Build succeeded 🎉' }
        failure { echo 'Build failed ❌' }
        always  { echo "Build complete at ${new Date()}" }
    }
}