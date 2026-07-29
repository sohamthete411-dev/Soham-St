nano Jenkinsfilepipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['development', 'production'], description: 'Target environment')
    }

    environment {
        APP_NAME = 'demo-app'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building ${env.APP_NAME}"
            }
        }

        stage('Tests') {
            parallel {
                stage('Unit') {
                    steps {
                        sh 'echo Running unit tests'
                    }
                }
                stage('Integration') {
                    steps {
                        sh 'echo Running integration tests'
                    }
                }
            }
        }

        stage('Approve') {
            when {
                expression { params.ENVIRONMENT == 'production' }
            }
            steps {
                input message: 'Deploy to production?'
            }
        }

        stage('Deploy') {
            steps {
                sh "echo Deploying to ${params.ENVIRONMENT}"
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
