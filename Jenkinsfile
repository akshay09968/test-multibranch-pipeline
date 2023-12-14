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
                script {
                    checkout([$class: 'GitSCM', branches: [[name: '*/main'], [name: '*/dev'], [name: '*/staging'], [name: '*/prod']], userRemoteConfigs: [[url: 'https://github.com/akshay09968/test-multibranch-pipeline.git', credentialsId: 'github']]])
                }
                echo "** Checkout completed by ${currentBuild.changeSets.collect { it.author.fullName }.join(', ')} **"
            }
        }
        // Add other stages specific to your pipeline
    }

    post {
        success {
            echo "Build successful! Initiated by ${currentBuild.changeSets.collect { it.author.fullName }.join(', ')}"
        }
        failure {
            echo "Build failed! Triggered by ${currentBuild.changeSets.collect { it.author.fullName }.join(', ')}"
        }
    }
}

triggers {
    githubPush(branchFilter: 'main, dev, staging, master')
}


