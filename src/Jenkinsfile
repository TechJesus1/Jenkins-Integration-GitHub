pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit and integration tests using a tool like Selenium
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Use a tool like SonarQube for code analysis
                echo 'Performing code analysis with SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                // Use a tool like OWASP ZAP for security scanning
                echo 'Performing security scan with OWASP ZAP'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2 instance)
                echo 'Deploying to staging environment'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                echo 'Running integration tests on staging environment'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2 instance)
                echo 'Deploying to production environment'
            }
        }
    }
    post {
        success {
            mail to: bhanu.psm27@gmail.com,
                 subject: "Jenkins Pipeline succeeded: ${currentBuild.fullDisplayName}",
                 body: "The Jenkins Pipeline ${env.JOB_NAME} succeeded! View the log at: ${env.BUILD_URL}"
        }
        failure {
            mail to: bhanu.psm27@gmail.com,
                 subject: "Jenkins Pipeline failed: ${currentBuild.fullDisplayName}",
                 body: "The Jenkins Pipeline ${env.JOB_NAME} failed. View the log at: ${env.BUILD_URL}"
        }
    }
}
