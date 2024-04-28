pipeline {
    agent any
    environment {
        BUILDER = "Gradle"
        TESTER = "BlazeMeter"
        ANALYSER = "Codacy"
        SCANNER = "Jit"
        STAGE_SRV = "AWS Development EC2 VPC"
        STAGE_TESTER = "Mocha"
        PRODUCTION_SRV = "AWS Production EC2 VPC"
    }
    stages {
        stage('Build'){
            steps{
                print("Compiling and packaging source code using $BUILDER")
            }
        }
        stage('Unit and Integration Tests'){
            steps{
                print("Running unit tests with $TESTER")
                print("Sending email...")
            }
            post{
                mail to: "cheeseburger199@gmail.com"
                subject: "Integration Test Status Email"
                body: "Integration tests passed by $TESTER."
                print("Email sent!")
            }
        }
        stage('Code Analysis'){
            steps{
                print("Performing code analysis using $ANALYSER")
            }
        }
        stage('Security Scan'){
            steps{
                print("Performing a vulnerability scan with $SCANNER")
                print("Sending email...")
            }
            post{
                mail to: "cheeseburger199@gmail.com"
                subject: "Security Scan Status Email"
                body: "$SCANNER found no vulnerabilities within the application."
                print("Email sent!")
            }
        }
        stage('Deploy to Staging'){
            steps{
                print("Deploying the application to the staging server: $STAGE_SRV")
            }
        }
        stage('Integration Tests on Staging')
            steps{
                print("Runing unit tests on $STAGE_SRV with $STAGE_TESTER")
            }
        stage('Deploy to Production'){
            steps{
                print("Application ready for production")
                print("Deploying application to $PRODUCTION_SRV")
            }
        }
    }
}