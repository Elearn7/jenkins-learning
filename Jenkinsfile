pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code retrieved from GitHub'
            }
        }

	stage('Branch Info') {
            steps {
                echo "Branch Name: ${env.BRANCH_NAME}"
		echo "Change ID: ${env.CHANGE_ID}"
		echo "Change Branch: ${env.CHANGE_BRANCH}"
		echo "Change Target: ${env.CHANGE_TARGET}"
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

	stage('PR Information') {
    	    steps {

        	echo "Branch: ${env.BRANCH_NAME}"

        	echo "Change ID: ${env.CHANGE_ID}"

        	echo "Change Target: ${env.CHANGE_TARGET}"

        	echo "Source Branch: ${env.CHANGE_BRANCH}"
    		}
	}

	stage('PR Lab') {
    	   steps {
              echo 'Running PR validation'
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
	}

	stage('Feature Branch Stage') {
   	   steps {
              echo 'Feature branch code'
    	   }
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
