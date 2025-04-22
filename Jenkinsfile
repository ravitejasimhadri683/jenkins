pipeline{
    agent any
    environment {
        ENV_VAR='pipeline.google.com'
    }
    stages{
        stage('Build'){
            steps{
                echo 'Building the Node.js application...'
                echo "Environment variable: ${ENV_VAR}"
            }
        }
        stage('Test'){
            environment {
                ENV_VAR='stage.google.com'
            }
            steps{  
                echo 'Running tests...'
                echo "Environment variable: ${ENV_VAR}"
            }
        }   
        stage('Deploy'){
            steps{
                echo 'Deploying the application...'
            }
        } 
    } 
}