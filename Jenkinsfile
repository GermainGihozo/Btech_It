pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo "Cloning repository..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building project..."
                bat 'dir'   // Windows equivalent of 'ls -la'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                bat 'echo Running tests here'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying..."
                bat 'echo Deployment step'
            }
        }
    }
}