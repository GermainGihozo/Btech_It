// pipeline {
//     agent any

//     stages {
//         stage('Clone') {
//             steps {
//                 echo "Cloning repository..."
//                 checkout scm
//             }
//         }

//         stage('Build') {
//             steps {
//                 echo "Building project..."
//                 bat 'dir'   // Windows equivalent of 'ls -la'
//             }
//         }

//         stage('Test') {
//             steps {
//                 echo "Running tests..."
//                 bat 'echo Running tests here'
//             }
//         }

//         stage('Deploy') {
//             steps {
//                 echo "Deploying..."
//                 bat 'echo Deployment step'
//             }
//         }
//     }
// }

pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Check JavaScript Syntax') {
            steps {
                script {
                    echo "Checking syntax for index.js..."

                    // Use bat for Windows
                    bat 'node --check index.js'
                }
            }
        }
    }

    post {
        success {
            echo "✔ No syntax errors found."
        }
        failure {
            echo "❌ Syntax error found in index.js"
        }
    }
}
