pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    // environment { 
    //     packageVersion = ''
    //     nexusURL = '172.31.8.127:8081'
    // }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'version', defaultValue: '', description: 'What is the artifact version?')
        string(name: 'environment', defaultValue: 'dev', description: 'What is environment?')
    }
    // build
    stages {
        stage('print version') {
            steps {
                sh """
                    echo "version: ${params.version}"
                    echo "environment: ${params.environment}"
                """
            }
        }
        
    }
    // post build
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        failure { 
            echo 'this runs when pipeline is failed, used generally to send some alerts'
        }
        success{
            echo 'I will say Hello when pipeline is success'
        }
    }
}