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

    post {
      success {
        echo "Build successful! Initiated by ${CHANGE_AUTHOR}"
      }
      failure {
        echo "Build failed! Triggered by ${CHANGE_AUTHOR}"
      }
    }
  }

  triggers {
    githubPush {
      branchFilter 'main, dev, staging, prod'
    }
  }

  scm {
    git {
      branchSource branchSet = [
        branch 'main',
        branch 'dev',
        branch 'staging',
        branch 'prod'
      ]
      domain 'github.com'
      credentialsId 'github' // Replace with your actual credentials ID
    }
  }
}
