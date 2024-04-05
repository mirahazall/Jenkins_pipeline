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
                    script {
                        sendEmailNotification('Unit and Integration Tests')
                    }
                }
                failure {
                    script {
                        sendEmailNotification('Unit and Integration Tests')
                    }
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
                    script {
                        sendEmailNotification('Security Scan')
                    }
                }
                failure {
                    script {
                        sendEmailNotification('Security Scan')
                    }
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

def sendEmailNotification(stageName) {
    def recipient = 'mira.hazal@outlook.com'
    def subject = "${stageName} Stage"
    def body = "${stageName} stage completed successfully."
    def logFile = currentBuild.rawBuild.getLogFile()
    
    // Read the log file content
    def logContent = readFile(logFile.toString())
    
    // Define the email body
    def emailBody = "${body}\n\nBuild Log:\n${logContent}"
    
    // Send the email with the log content as attachment
    mail to: recipient,
         subject: subject,
         body: emailBody
}
