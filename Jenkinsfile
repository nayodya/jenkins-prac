pipeline{
    agent any

    environment{
        APP_NAME = 'MyApp'
        DEPLOY_ENV = 'production'
    }

    tools{
        mvn 'Maven_3_9_6'
    }

    stages{
        stage('audit check'){
            steps{
                echo 'performing audit checks ...'
                sh '''
                    git --version
                    java -version
                    mvn -version
                '''
            }
        }

        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('build'){
            parallel{
                stage('linux-build'){
                    agent any
                    steps{
                        echo 'building the app for linux ...'
                    }
                }
                stage('windows-build'){
                    agent any
                    steps{
                        echo 'building the app for windows ...'
                    }
                }
                stage('mac-build'){
                    agent any
                    steps{
                        echo 'building the app for mac ...'
                    }
                }
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