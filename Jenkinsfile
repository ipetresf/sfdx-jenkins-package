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
                withCredentials([file(credentialsId: env.server_key_file, variable: 'server_key_file')]) {
                    rc = command "${toolbelt}/sfdx force:auth:jwt:grant --instanceurl ${SF_INSTANCE_URL} --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --setalias HubOrg"
                    if (rc != 0) {
                        error 'Salesforce dev hub org authorization failed.'
                    }
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