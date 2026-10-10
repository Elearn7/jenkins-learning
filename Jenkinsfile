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

        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Deploy') {

            when {
                branch 'main'
            }

            steps {
                echo 'Deploying to production'
            }
        }
    }
}
