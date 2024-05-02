pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Build the code using Maven.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Run tests using JUnit and Selenium.'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyse code with SonarQube.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Perform security scan with OWASP ZAP.'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploy application to AWS EC2 staging instance.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Run integration tests in staging environment.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploy application to AWS EC2 production instance.'
            }
        }
    }
    post {
        success {
            mail to: 'ruthnenice@gmail.com',
                  subject: "Build Successful",
                  body: "The build was successful."
        }
        failure {
            mail to: 'ruthnenice@gmail.com',
                  subject: "Build Failed",
                  body: "The build failed."
        }
    }
}
