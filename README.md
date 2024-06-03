# Jenkins Pipeline README

This Jenkins pipeline is designed to automate the build, testing, analysis, and deployment process of a software application. It consists of several stages, each performing a specific task in the software development lifecycle.

## Pipeline Stages

### Build
- This stage builds the code using Maven by executing the `mvn clean package` command.

### Unit and Integration Tests
- This stage runs unit tests using JUnit and integration tests using a tool like Selenium by executing the `mvn test` command.

### Code Analysis
- This stage performs code analysis using a tool like SonarQube.

### Security Scan
- This stage performs security scanning using a tool like OWASP ZAP.

### Deploy to Staging
- This stage deploys the application to a staging environment, such as an AWS EC2 instance.

### Integration Tests on Staging
- This stage runs integration tests on the staging environment.

### Deploy to Production
- This stage deploys the application to a production environment, such as an AWS EC2 instance.

## Post-Build Actions

### Success
- If the pipeline succeeds, an email notification is sent to bhanu.psm27@gmail.com with the subject "Jenkins Pipeline succeeded: {pipeline full display name}" and a body containing a link to view the build log.

### Failure
- If the pipeline fails, an email notification is sent to bhanu.psm27@gmail.com with the subject "Jenkins Pipeline failed: {pipeline full display name}" and a body containing a link to view the build log.

