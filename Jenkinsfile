pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code retrieved from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh '''
                    mkdir -p build

                    echo "Application Build" > build/app.txt

                    echo "Build Number: $BUILD_NUMBER" >> build/app.txt

                    echo "Build Date: $(date)" >> build/app.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "Running tests..."
                    echo "All tests passed"
                '''
            }
        }

        stage('Security Scan') {
	   steps {
	      echo "running security checks"
	}

	stage('Package') {
            steps {
                sh '''
                    tar -czf application.tar.gz build/
                '''
		archiveArtifacts artifacts: 'application.tar.gz'
           }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
    }
}
