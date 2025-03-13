pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    try {
                        checkout([$class: 'GitSCM',
                            branches: [[name: '*/main']],
                            userRemoteConfigs: [[url: 'https://github.com/shreyamp01/PES1UG22CS574_Jenkins.git']]
                        ])
                    } catch (err) {
                        error "Git checkout failed: ${err}"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    try {
                        sh 'g++ ./main/hello.cpp -o output'
                        echo 'Build successful'
                    } catch (err) {
                        error "Build failed: ${err}"
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    try {
                        sh './output'
                        echo 'Tests executed successfully'
                    } catch (err) {
                        error "Test execution failed: ${err}"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add deployment commands here if necessary
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for errors.'
        }
    }
}
