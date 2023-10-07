pipeline {
    agent {
        docker {
            image 'node:16'
        }
    }
    stages {
	stage('Preparation') {
            steps {
                // Workaround for npm cache issue
                sh 'echo "Setting up permissions for npm cache"'
                sh 'chown -R node:node /home/node || echo "Handled permission issue"'
                sh 'npm config set cache /home/node/.npm --global'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install --save'
            }
        }
    }
}
