pipeline{
    agent any
    parameters {
        string defaultValue: 'dev', description: 'dev test qa prod', name: 'environment'
    }
    stages{
        stage('checkout stage'){
            steps{
                    checkout scmGit(
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[url: 'https://github.com/GitPasss/Jenkins-script.git']])
            }
        }
        stage('script usage1'){
            steps{
                bat'''
                helloworld.bat
                '''
            }
        }
        stage('script usage2') {
            steps {
                bat "script.bat ${params.environment}"
            }
        }
        stage('script usage3'){
            steps{
                script{
                    def values = ['uat', 'dev' , 'prod']
                    for (n in values) {
                        bat "loop-script.bat $n"
                    }
                }
            }
        }
    }
}
