pipeline {
    agent any

    stages {

        stage('GitHub Pipeline') {
            steps {
                echo 'Pipeline loaded from GitHub'
<<<<<<< HEAD
		echo 'Pipeline loaded from GitH*b'echo 'Pipeline loaded from GitH*b'
		echo 'Version 2 of my pipeline'*            
			}
=======
		echo 'Version 2 of my pipeline'         
		 }
>>>>>>> 63d1490 (proper update)
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
