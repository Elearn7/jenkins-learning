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

               
