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
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password') 
    }
    // triggers { cron('*/1 * * * *') }
    // triggers { pollSCM('*/1 * * * *') }
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
        stage('Deploying To Prod') {
            input {
                message "Should we continue?"
                ok "YES"
                submitter "admin"
                parameters {
                    string(name: 'PERSON', defaultValue: 'No', description: 'YES or NO to proceed')
                }
            }
            steps {
                sh 'echo Running On Prod'
            }
        }
        
    } 
}