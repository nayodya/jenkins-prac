pipeline{
    agent any

    environment{
        APP_NAME = 'MyApp'
        DEPLOY_ENV = 'production'
    }

    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('build'){
            steps{
                echo 'building the app ... ${APP_NAME} for ${DEPLOY_ENV}'
            }
        }
        stage('tests'){
            steps{
                echo 'testing the app ...'
            }
        }
        stage('deploy'){
            input{
                message 'Are you sure you want to deploy to ${DEPLOY_ENV}?'
                ok 'Yes, deploy now'
                parameters{
                    string(name: 'DEPLOYER_NAME', defaultValue: 'admin', description: 'Name of the person deploying')
                }
            }
        }
        
    }

    post{
        success{
            echo 'The pipeline has succeeded!'
        }
        failure{
            echo 'The pipeline has failed!'
        }
    }
}