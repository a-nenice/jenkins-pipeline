pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven. Maven is used to compile and package the Java application.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit and integration tests with Selenium. JUnit is used for unit testing, while Selenium handles integration tests to ensure components interact correctly.'
            }
            post {
                always {
                    emailext (
                        to: "ruthnenice@gmail.com",
                        subject: "Test Results Notification",
                        body: "The tests stage has completed. Please check the Jenkins dashboard for detailed results.",
                        attachmentsPattern: '**/target/surefire-reports/*.xml',
                        mimeType: 'text/html'
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analysing code with SonarQube. SonarQube provides a detailed report of code quality and potential bugs.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP. OWASP ZAP is used to detect security vulnerabilities in the application.'
            }
            post {
                always {
                    emailext (
                        to: "ruthnenice@gmail.com",
                        subject: "Security Scan Notification",
                        body: "The security scan stage has completed. Please check the Jenkins dashboard for detailed results.",
                        attachmentsPattern: '**/zap-reports/*.html',
                        mimeType: 'text/html'
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to AWS EC2 staging instance. The AWS EC2 service is used to host the staging environment.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in the staging environment to validate production readiness. Integration tests ensure the app behaves as expected in a setup that mimics the production environment.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to AWS EC2 production instance. The production deployment uses AWS EC2, ensuring the application is available for end users.'
            }
        }
    }
}
