pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Building the code using Node Package Manager(npm)"
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests to ensure the code functions as expected using Mocha and Chai"
                echo "Running integration tests using Sinon.js and MockServer"
            }

            post {
                success {
                    // Send success email notification with logs
                    emailext (
                        subject: 'Test Stage Successful',
                        body: 'Test stage completed successfully.',
                        attachLog: true,
                        to: 'mira.hazal@outlook.com'
                    )
                }
                failure {
                    // Send failure email notification with logs
                    emailext (
                        subject: 'Test Stage Failed',
                        body: 'Test stage failed. See the attached logs for details.',
                        attachLog: true,
                        to: 'mira.hazal@outlook.com'
                    )
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing code to ensure it meets industry standards using ESLint"
            }
        }
        
        stage('Security Scan') {
            steps {
                echo "Performing security scan using NPM Audit"
            }
            
            post {
                success {
                    // Send success email notification with logs
                    emailext (
                        subject: 'Security Scan Stage Successful',
                        body: 'Security Scan stage completed successfully.',
                        attachLog: true,
                        to: 'mira.hazal@outlook.com'
                    )
                }
                failure {
                    // Send failure email notification with logs
                    emailext (
                        subject: 'Security Scan Stage Failed',
                        body: 'Security Scan stage failed. See the attached logs for details.',
                        attachLog: true,
                        to: 'mira.hazal@outlook.com'
                    )
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a staging server, using Docker Compose"
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging environment using Jest"
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to a production server using Docker Compose"
            }
        }
    }
}
