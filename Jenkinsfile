pipeline{
    agent any

    parameters{
        booleanParam(name: 'RELEASE', defaultValue: false, description: 'Is this a release build?')
        }

    environment{
        NEW_RELEASE = "1.0.0"
        INITIAL_RELEASE = "0.9.0"
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
            environment{
                VERSION_SUFFIX = ""
            }
            steps{
                echo 'building the app ...'
                sh 'mvn -f pom.xml clean package'
            }
        }

        stage('tests'){
            steps{
                echo 'testing the app ...'
            }
        }
        stage('Publish Artifacts'){
            when {
                expression { return params.RELEASE }
            }
            steps{
                echo 'Publishing the build artifacts ...'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
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