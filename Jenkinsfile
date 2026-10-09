pipeline {
    agent any

    stages {

        stage('GitHub Pipeline') {
            steps {
                echo 'Pipeline loaded from GitHub'
            }
        }

        stage('Environment Info') {
            steps {
                sh '''
                    echo "Build Number: $BUILD_NUMBER"
                    echo "Node Name: $NODE_NAME"
                    hostname
                '''
            }
        }

    }
}
