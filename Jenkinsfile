pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                echo 'Using Maven to compile and package the code.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                echo 'Using JUnit for unit tests and TestNG for integration tests.'
            }
            post {
                always {
                    mail to: 'Cold2thev@gmail.com',
                         subject: "Pipeline Test Stage Execution: ${currentBuild.fullDisplayName}",
                         body: "Status of the Test Stage: ${currentBuild.currentResult}\n\nPlease check the attached log for details.",
                         attachLog: true
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code for quality and standards...'
                echo 'Using SonarQube for static code analysis.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                echo 'Using OWASP ZAP for security vulnerabilities.'
            }
            post {
                always {
                    mail to: 'Cold2thev@gmail.com',
                         subject: "Pipeline Security Scan Stage Execution: ${currentBuild.fullDisplayName}",
                         body: "Status of the Security Scan Stage: ${currentBuild.currentResult}\n\nPlease check the attached log for details.",
                         attachLog: true
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                echo 'Deploying to an AWS EC2 instance.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                echo 'Using Selenium for end-to-end tests in the staging environment.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                echo 'Deploying to a production AWS EC2 instance.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
            mail to: 'Cold2thev@gmail.com',
                 subject: "Pipeline Execution: ${currentBuild.fullDisplayName}",
                 body: "Final Status: ${currentBuild.currentResult}\n\nPlease check the attached log for details.",
                 attachLog: true
        }
    }
}
