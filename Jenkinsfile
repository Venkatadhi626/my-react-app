pipeline {
    agent any
    tools {
        nodejs "NodeJS 20" // NodeJS version configured in Jenkins Global Tool Configuration
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: '*/master', url: 'https://github.com/Venkatadhi626/my-react-app.git'
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('Test') {
            steps {
                bat 'npm test -- --watchAll=false'
            }
        }
        stage('Serve (Optional)') {
            steps {
                bat 'start /B npm start'
                bat 'timeout /t 10' // Wait for app to start
            }
        }
    }
    post {
        always {
            bat 'taskkill /IM node.exe /F || exit 0' // Kill node process to avoid port conflicts
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}