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
                // Run unit tests using JUnit
                sh 'mvn test'

                // Run integration tests using Selenium
                sh 'mvn selenium:test'
            }
        }

        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool using Jenkins plugin (e.g., Checkstyle)
                checkstyle canRunOnFailed: true, defaultEncoding: 'UTF-8', pattern: '**/*.java'
            }
        }

        stage('Security Scan') {
            steps {
                // Perform security scan using OWASP ZAP
                sh 'zap-cli --start --quickurl http://localhost:8080 --spider --output /zap/spider-output.html'
                sh 'zap-cli --quickscan --output /zap/scan-output.html'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server using AWS CLI
                sh 'aws ecs deploy ...' // Replace '...' with actual AWS ECS deployment command
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment using JMeter
                sh 'jmeter -n -t /path/to/jmeter/testplan.jmx -l /path/to/results/output.jtl'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server using AWS CLI
                sh 'aws ecs deploy ...' // Replace '...' with actual AWS ECS deployment command
            }
        }
    }

    post {
        success {
            // Send success notification email
            emailext (
                to: 'bhanu.psm27@gmail.com',
                subject: "Pipeline Successful - ${currentBuild.fullDisplayName}",
                body: "The pipeline has completed successfully.",
                attachLog: true
            )
        }
        failure {
            // Send failure notification email
            emailext (
                to: 'bhanu.psm27@gmail.com',
                subject: "Pipeline Failed - ${currentBuild.fullDisplayName}",
                body: "The pipeline has failed. Check the Jenkins console output for details.",
                attachLog: true
            )
        }
    }
}
