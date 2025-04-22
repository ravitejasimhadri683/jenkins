pipeline{
    agent any
    environment {
        ENV_VAR='pipeline.google.com'
        SSH_CRED=credentials('ssh-cred')
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        /* password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password') */
    }
    stages{
        stage('Build'){
            steps{
                sh '''
                    echo 'Building the Node.js application...'
                    echo "Environment variable: ${ENV_VAR}"
                    
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