pipeline {
    agent any

    tools {
        nodejs "NodeJS 20" // match with Global Tools name
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Venkatadhi626/my-react-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy (Serve Locally)') {
            steps {
                bat 'npx serve -s build -l 5000'
            }
        }
    }
}












