pipeline{
    agent any
    environment {
        ENV_VAR='pipeline.google.com'
        SSH_CRED=credentials('ssh-cred')
    }
    stages{
        stage('Build'){
            steps{
                sh '''
                    echo 'Building the Node.js application...'
                    echo "Environment variable: ${ENV_VAR}"
                    env
                '''
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