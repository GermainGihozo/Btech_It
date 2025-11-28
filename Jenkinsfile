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
        // This makes Jenkins run automatically when GitHub changes are pushed
        pollSCM('* * * * *')   // every 1 minute (or use GitHub webhook)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check JavaScript Syntax') {
            steps {
                script {
                    echo "Checking syntax for index.js..."

                    // This command checks only syntax, no package needed
                    sh 'node --check index.js'
                }
            }
        }
    }

    post {
        success {
            echo "✔ No syntax errors found in index.js"
        }
        failure {
            echo "❌ Syntax error found in index.js"
        }
    }
}
