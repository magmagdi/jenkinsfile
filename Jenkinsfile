pipeline {

    agent any

    environment {

        APP_NAME = 'my-awesome-app'

        APP_VERSION = '1.0.0'

        BUILD_TIMESTAMP = sh(script: 'date +%Y%m%d-%H%M%S', returnStdout: true).trim()

    }



    stages {

        stage('Checkout') {

            steps {

                echo "Checking out ${APP_NAME} v${APP_VERSION}"
                echo "Build timestamp: ${BUILD_TIMESTAMP}"
                echo "Build number: ${env.BUILD_NUMBER}"      
                echo "Job name: ${env.JOB_NAME}"              

            }

        }



        stage('Build') {

            steps {

                echo 'Compiling the application...'

                sh '''

                    echo "Simulating build process..."

                    mkdir -p build/output

                    echo "Build artifact content - version ${APP_VERSION}" > build/output/app.txt

                    echo "Build complete!"

                '''

            }

        }



        stage('Test') {

            parallel {

                stage('Unit Tests') {

                    steps {

                        echo 'Running unit tests...'

                        sh '''

                            echo "Test 1: User login......... PASSED"

                            echo "Test 2: User logout........ PASSED"

                            echo "Test 3: Data validation.... PASSED"

                            echo "-------------------------------"

                            echo "3/3 tests passed!"

                        '''

                    }

                }

                stage('Integration Tests') {

                    steps {

                        echo 'Running integration tests...'

                        sh '''

                            echo "Test 1: API endpoint /health... PASSED"

                            echo "Test 2: Database connection.... PASSED"

                            echo "-------------------------------"

                            echo "2/2 tests passed!"

                        '''

                    }

                }

            }

        }



        stage('Security Scan') {

            steps {

                echo 'Running security checks...'

                sh '''

                    echo "Scanning for vulnerabilities..."

                    echo "No critical vulnerabilities found."

                    echo "Security scan: PASSED"

                '''

            }

        }



        stage('Deploy to Staging') {

            steps {

                echo 'Deploying to staging environment...'

                sh '''

                    echo "Uploading artifact to staging server..."

                    echo "Running smoke tests on staging..."

                    echo "Staging deployment: SUCCESS"

                '''

            }

        }



        stage('Approval') {

            steps {

                echo 'Waiting for manual approval to deploy to production...'

                echo 'Auto-approved for demo purposes.'

            }

        }



        stage('Deploy to Production') {

            steps {

                echo 'Deploying to production...'

                sh '''

                    echo "============================================="

                    echo "  PRODUCTION DEPLOYMENT"

                    echo "  App: ${APP_NAME}"

                    echo "  Version: ${APP_VERSION}"

                    echo "  Timestamp: $(date)"

                    echo "============================================="

                    echo "Deployment successful!"

                '''

            }

        }

    }



    post {

        success {

            echo "Pipeline completed SUCCESSFULLY! ${APP_NAME} v${APP_VERSION} is now live."

        }

        failure {

            echo 'Pipeline FAILED! Check the logs above for details.'

        }

        always {

            echo 'Pipeline execution finished. Cleaning up workspace...'
        }

    }

}