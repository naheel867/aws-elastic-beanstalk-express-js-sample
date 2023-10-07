pipeline {
  agent {
    docker {
      image 'node:16'
      // Run as 'node' user inside the container
      args '-u node'
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
        sh 'npm install --save'
      }
    }
  }
}
