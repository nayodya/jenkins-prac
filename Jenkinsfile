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
            steps{
                echo 'deploying the app ...'
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