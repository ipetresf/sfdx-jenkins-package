pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'sfdx --version'
            }
        }
        stage('Test') { 
            steps {
                sh 'echo \'Test\''
            }
        }
        stage('Deploy') { 
            steps {
                sh 'echo \'Deploy\''
            }
        }
    }
}