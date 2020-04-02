def toolbelt = tool 'toolbelt'

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
                sh 'echo ${server_key_file}'
                withCredentials([file(credentialsId: env.server_key_file, variable: 'sfdx_ork_key')]) {
                    sh 'echo ${sfdx_ork_key}'
                }
            }
        }
    }
}

def command(script) {
    if (isUnix()) {
        return sh(returnStatus: true, script: script);
    } else {
        return bat(returnStatus: true, script: script);
    }
}