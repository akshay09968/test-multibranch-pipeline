pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo "Started by GitLab push by ${GIT_PUSHER_NAME}"
      }
    }
  }

  post {
    success {
      echo "Build successful!"
    }
    failure {
      echo "Build failed!"
    }
  }
}
