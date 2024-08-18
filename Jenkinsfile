pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Build - Build the code using a build automation tool to compile and package your code. Tool: Maven."
            }
        }
        stage("Unit and Integration Tests"){
            steps{
                echo "Run unit tests to ensure the code functions as expected and run integration tests to ensure the different components of the application work together as expected. Tool: Selenium."
            }
            post {
                always{
                    script{                 
                        emailext subject: "Test Status: ${currentBuild.currentResult}",
                            to: 'siweiluo086@gmail.com', 
                            body: "The current build result is: ${currentBuild.currentResult}. \n\nDetails:\n${currentBuild.fullDisplayName}\n${currentBuild.absoluteUrl}",
                            attachmentsPattern: '**/test.log'
                    }                   
                }
            }
        }
        stage("Code Analysis"){
            steps{
                echo "integrate a code analysis tool to analyse the code and ensure it meets industry standards. Tool: GitLab."
            }
        }
        stage("Security Scan"){
            steps{
                echo "Perform a security scan on the code using a tool to identify any vulnerabilities. Tool: Snyk."
            }
            post {
                 always{
                    script{                 
                        emailext subject: "Security Scan Status: ${currentBuild.currentResult}",
                            to: 'siweiluo086@gmail.com', 
                            body: "The current build result is: ${currentBuild.currentResult}. \n\nDetails:\n${currentBuild.fullDisplayName}\n${currentBuild.absoluteUrl}",
                            attachmentsPattern: '**/security.log'
                    }                   
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
