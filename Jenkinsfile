pipeline {

    agent any

    environment {
        APP_NAME = 'jenkins-learning'
        DEPLOY_ENV = 'none'
    }

    stages {

        stage('Branch Information') {
            steps {
                echo "Branch Name: ${env.BRANCH_NAME}"
                echo "Application: ${env.APP_NAME}"
            }
        }

        stage('Environment Selection') {
            steps {
                script {

                    if (env.BRANCH_NAME == 'main') {
                        env.DEPLOY_ENV = 'production'
                    } else {
                        env.DEPLOY_ENV = 'development'
                    }

                    echo "Target Environment: ${env.DEPLOY_ENV}"
                }
            }
        }

        stage('Branch Logic') {
            steps {
                script {

                    if (env.BRANCH_NAME.startsWith('feature/')) {

                        echo "Feature Branch Build"

                    } else {

                        echo "Main/Develop Branch Build"

                    }

                }
            }
        }

        stage('Build') {
            steps {

                sh '''
                    echo "Application: $APP_NAME"
                    echo "Branch: $BRANCH_NAME"
                    echo "Build Number: $BUILD_NUMBER"
                    echo "Building application..."
                '''

            }
        }

	stage('PR Lab') {
    	   steps {
              echo 'Running PR validation'
    	   }
	}

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Deploy') {

            when {

                anyOf {
                    branch 'main'
                    branch 'develop'
                }

            }

            steps {
                echo "Deploying to ${env.DEPLOY_ENV}"
            }
        }
    }

    post {

        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }

        always {
            echo 'Pipeline execution finished'
        }

    }
}
