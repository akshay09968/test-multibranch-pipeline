// pipeline {
//     agent any
//     environment {
//         BUILD_USER = "${BUILD_USER}"
//     }
//     stages {
//         stage("Echo a line") {
//             steps {
//                 echo 'This is step one'
//             }
//         }

//         stage("Run a command") {
//             steps {
//                 sh 'pwd'
//             }
//         }

//         stage("Run multiple commands") {
//             steps {
//                 sh '''pwd
//                     ls
//                     date
//                     cat'''
//             }
//         }

//         stage("D") {
//             steps {
//                 echo "========executing A========"
//             }
//         }
//     }
//     post {
//         always {
//             echo "========always========"
//         }
//         success {
//             script {
//                 echo "========pipeline executed successfully ========"
//                 echo "User who pushed changes: ${BUILD_USER}"
//             }
//         }
//         failure {
//             script {
//                 echo "========pipeline execution failed========"
//                 echo "User who pushed changes: ${BUILD_USER}"
//             }
//         }
//     }
// }



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


