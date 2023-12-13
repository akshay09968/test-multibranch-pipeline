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
        stage('Build') {
            steps {
                script {
                    // Option 1: Use GIT_PUSHER_NAME environment variable (requires no additional plugins)
                    String username = env.GIT_PUSHER_NAME
                    echo "Build started by: $username"

                    // Option 2: Use Jenkins Build User Vars Plugin (requires plugin installation)
                    // def user = env.BUILD_USER
                    // echo "Build started by: $user"

                    // Option 3: Custom script to retrieve username (more flexibility, but complex)
                    // String username = sh(returnStdout: true, script: 'git log -1 --pretty=format:"%an"')
                    // echo "Build started by: $username"

                    // Your build steps here...
                }
            }
        }
    }

    post {
        success {
            // You can use the username variable in post-build steps as well
            echo "Build completed successfully by ${env.GIT_PUSHER_NAME}"
        }
    }
}
