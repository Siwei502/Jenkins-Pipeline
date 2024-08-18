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
 /*           post {
                always{
                  //  mail to: "siweiluo086@gmail.com", subject: "Build Status: ${currentBuild.currentResult}", body: "The build status is: ${currentBuild.currentResult}. Please find the details attached."
                script{
                    def mailRecipients = 'siweiluo086@gmail.com'
                    emailext subject: "${currentBuild.currentResult}",
                        to: "${mailRecipients}", 
                        body: "${currentBuild.currentResult}"
                }                   

            }*/

                success {
                    echo "Tests completed successfully!"
                    emailext( to: "siweiluo086@gmail.com",
                        subject: "Test Status: SUCCESS",
                        body: "Unit and integration tests passed.",
                        //attachLog: true,
                        attachmentsPattern: '**/*.log')
                    //archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
                    //emailext attachLog: true, attachmentsPattern: '**/*.log'
                }
                failure {
                    echo "Tests failed."
                        emailext( to: "siweiluo086@gmail.com",
                        subject: "Test Status: FAILURE",
                        body: "Unit and integration tests failed.",
                    //archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
                        //attachLog: true,
                        attachmentsPattern: '**/*.log')
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
                    emailext( to: "siweiluo086@gmail.com",
                        subject: "Secirity Scan Status: SUCCESS",
                        body: "Secirity Scan passed.",
                    //archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
                        //attachLog: true,
                        attachmentsPattern: '**/*.log')
                }
                failure {
                    echo "Secirity Scan failed."
                    emailext( to: "siweiluo086@gmail.com",
                        subject: "Secirity Scan Status: FAILURE",
                        body: "Secirity Scan failed.",
                    //archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
                        //attachLog: true,
                        attachmentsPattern: '**/*.log')
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

