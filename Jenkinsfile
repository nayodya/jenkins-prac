pipeline {
    agent {
        docker { image 'maven:3.9.4-openjdk-17' }
    }
    stages {
        stage('Build Backend') {
            steps {
                dir('backend') {   // Move into backend folder
                    sh 'mvn clean install'
                }
            }
        }
    }
}
