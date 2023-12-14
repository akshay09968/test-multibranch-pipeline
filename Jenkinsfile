pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
        echo "** Checkout completed by ${CHANGE_AUTHOR} **"
      }
    }
    // Add other stages specific to your pipeline
  }

  post {
    success {
      echo "Build successful! Initiated by ${CHANGE_AUTHOR}"
    }
    failure {
      echo "Build failed! Triggered by ${CHANGE_AUTHOR}"
    }
  }

  triggers {
    githubPush {
      branchFilter 'main, dev, staging, prod'
    }
  }

  options {
    skipDefaultCheckout() // This avoids redundant checkout, as you are already checking out in the 'Checkout' stage
  }

  scm {
    git {
      branches('main', 'dev', 'staging', 'master') // Correct syntax for defining branches
      userRemoteConfigs([
        [url: 'https://github.com/akshay09968/test-multibranch-pipeline.git', credentialsId: 'github']
      ])
    }
  }
}
