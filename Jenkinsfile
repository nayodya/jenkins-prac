pipeline{
    agent any

    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('build'){
            steps{
                echo 'building the app ...'
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