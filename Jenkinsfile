pipeline {
    agent {
        docker {
            image 'node:16'
            // Run as the Jenkins user inside the container (using your provided UID and GID)
            args '-u 115:121'
        }
    }
    stages {
        stage('Preparation') {
            steps {
                // Workaround for npm cache issue
                sh 'echo "Setting up permissions for npm cache"'
                // Adjusted the path based on typical Node.js Docker image structure
                sh 'mkdir -p /home/node/.npm && chown -R 115:121 /home/node/.npm || true'
                sh 'npm config set cache /home/node/.npm'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install --save'
            }
        }
    }
}

