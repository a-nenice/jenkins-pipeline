pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven to compile and package the application.'
                // Placeholder: sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using JUnit and integration tests using Selenium to ensure functional and component integration.'
                // Placeholder: sh 'mvn test'
            }
            post {
                always {
                    emailext (
                        to: 'ruthnenice@gmail.com',
                        subject: "${env.JOB_NAME} - ${env.BUILD_NUMBER} - Tests Stage Status",
                        body: """<p>Tests Stage Completed: $BUILD_STATUS</p>
                                 <p>Check console output at <a href='$BUILD_URL'>Build URL</a></p>""",
                        attachmentsPattern: '**/target/surefire-reports/*.xml',
                        mimeType: 'text/html'
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analysing code with SonarQube to ensure it meets industry standards.'
                // Placeholder: sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP to identify any vulnerabilities in the code.'
                // Placeholder: sh 'zap.sh'
            }
            post {
                always {
                    emailext (
                        to: 'ruthnenice@gmail.com',
                        subject: "${env.JOB_NAME} - ${env.BUILD_NUMBER} - Security Scan Stage Status",
                        body: """<p>Security Scan Stage Completed: $BUILD_STATUS</p>
                                 <p>Check console output at <a href='$BUILD_URL'>Build URL</a></p>""",
                        attachmentsPattern: '**/zap-reports/*.html',
                        mimeType: 'text/html'
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to AWS EC2 staging instance.'
                // Placeholder: sh 'deploy_staging.sh'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in the staging environment to validate production readiness.'
                // Placeholder: sh 'run_integration_tests.sh'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to AWS EC2 production instance.'
                // Placeholder: sh 'deploy_production.sh'
            }
        }
    }
}
