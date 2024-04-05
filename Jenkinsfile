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
    // Send success email notification with logs as attachment
    def recipient = 'mira.hazal@outlook.com'
    def subject = 'Test Stage Successful'
    def body = 'Test stage completed successfully.'
    def logFile = currentBuild.rawBuild.getLogFile()
    
    // Read the log file content
    def logContent = readFile(logFile)
    
    // Define the email body
    def emailBody = "${body}\n\nBuild Log:\n${logContent}"
    
    // Send the email with the log content as attachment
    mail to: recipient,
         subject: subject,
         body: emailBody
}
                failure {
                    // Send failure email notification with logs
                        mail to: 'mira.hazal@outlook.com',
                        subject: 'Test Stage Failed',
                        body: 'Test stage failed. See the attached logs for details.',
                        attachments: [file: currentBuild.rawBuild.getLogFile()]
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
                        mail to: 'mira.hazal@outlook.com',
                        subject: 'Security Scan Stage Successful',
                        body: 'Security Scan stage completed successfully.',
                        attachments: [file: currentBuild.rawBuild.getLogFile()]
                }
                failure {
                        mail to: 'mira.hazal@outlook.com',
                        subject: 'Security Scan Stage Failed',
                        body: 'Security Scan stage failed. See the attached logs for details.',
                        attachments: [file: currentBuild.rawBuild.getLogFile()]
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
