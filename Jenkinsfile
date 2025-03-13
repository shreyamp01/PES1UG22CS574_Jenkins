pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/shreyamp01/PES1UG22CS574_Jenkins.git']]])
            }
        }
        
        stage('Build') {
            steps {
                build 'PES1UG22CS574-1'
                sh 'g++ ./main/hello1.cpp -o output'
            }
        }

        stage('Test') {
            steps {
                sh './output'
            }
        }

        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }

    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
change necessary details
