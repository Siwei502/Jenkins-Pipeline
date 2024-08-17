pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Build - Build the code using a build automation tool to compile and package your code. Tool: Maven."
            }
        }
        stage("Unit and Intefration Tests"){
            steps{
                echo "Run unit tests to ensure the code functions as expected and run integration tests to ensure the different components of the application work together as expected. Tool: Selenium."
            }
            post {
                success {
                    echo "Tests completed successfully!"
                    mail to: "siweiluo086@gmail.com",
                        subject: "Test Status: SUCCESS",
                        body: "Unit and integration tests passed.",
                        attachmentsPattern: '**/*'
                    //archiveArtifacts artifacts: '**/*', allowEmptyArchive: true

                }
                failure {
                    echo "Tests failed."
                        mail to: "siweiluo086@gmail.com",
                        subject: "Test Status: FAILURE",
                        body: "Unit and integration tests failed.",
                    //archiveArtifacts artifacts: '**/*', allowEmptyArchive: true
                        attachmentsPattern: '**/*'
                }
            }
        }
        stage("Code Analysis"){
            steps{
                echo "- integrate a code analysis tool to analyse the code and ensure it meets industry standards. Tool: GitLab."
            }
        }
        stage("Secirity Scan"){
            steps{
                echo "Perform a security scan on the code using a tool to identify any vulnerabilities. Tool: Snyk."
            }
            post {
                success {
                    echo "Secirity Scan successfully!"
                    mail to: "siweiluo086@gmail.com",
                        subject: "Secirity Scan Status: SUCCESS",
                        body: "Secirity Scan passed.",
                    //archiveArtifacts artifacts: '**/*', allowEmptyArchive: true
                        attachmentsPattern: '**/*'
                }
                failure {
                    echo "Secirity Scan failed."
                    mail to: "siweiluo086@gmail.com",
                        subject: "Secirity Scan Status: FAILURE",
                        body: "Secirity Scan failed.",
                    //archiveArtifacts artifacts: '**/*', allowEmptyArchive: true
                        attachmentsPattern: '**/*'
                }
            }
        }
        stage("Deploy to Staging"){
            steps{
                echo "deploy the application to a staging server. Tool: AWS."
            }
        }
        stage("Integration Tests on Staging"){
            steps{
                echo "run integration tests on the staging environment to ensure the application functions as expected in a production-like environment."
            }
        }
        stage("Deploy to Production"){
            steps{
                echo "Deploy the application to a production server. Tool: Terraform."
            }
        }
    }
}
