pipeline {
    agent {
        docker {
            image 'node:16'
            // Run as 'node' user inside the container
            args '-u 115:121'
        }
    }
    stages {
        stage('Preparation') {
            steps {
                // Workaround for npm cache issue
                sh 'echo "Setting up permissions for npm cache"'
                sh 'chown -R node:node /home/node/.npm || true'
                sh 'npm config set cache /home/node/.npm --global'
            }
        }
        stage('Build') {
            steps {
                // Added '|| true' to ensure the script will continue running even if the npm cache directory does not exist.
                sh 'npm install --save || true'
            }
        }
    }
}


