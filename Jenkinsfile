pipeline {
    agent any
    environment {
        // You can specify environment variables here, such as Node version
        NODE_VERSION = '20'  // Set the Node.js version you want to use
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rajitaroy/Jenkins-check.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js and npm
                    sh 'npm install'  // Or 'yarn install' if you are using Yarn
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Run the build script to bundle the React app
                    sh 'npm run build'  // Or 'yarn build' if using Yarn
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests if any are defined
                    sh 'npm test -- --coverage'  // Or 'yarn test' if using Yarn
                }
            }
        }
    }
    post {
        failure {
            // Send failure notification if the build fails
            mail to: 'rajitaroy660@gmail.com', subject: 'Build Failed', body: 'Check Jenkins logs for details.'
        }
        success {
            // Send success notification if the build is successful
            mail to: 'rajitaroy660@gmail.com', subject: 'Build Succeeded', body: 'The build has been successfully completed.'
        }
    }
}
