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
                sh 'echo ${SF_CONSUMER_KEY}'
                sh 'echo ${SF_USERNAME}'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'echo \'Deploy\''
            }
        }
    }
}