pipeline {
    agent any
    environment {
        BUILD_USER = "${BUILD_USER}"
    }
    stages {
        stage("Echo a line") {
            steps {
                echo 'This is step one'
            }
        }

        stage("Run a command") {
            steps {
                sh 'pwd'
            }
        }

        stage("Run multiple commands") {
            steps {
                sh '''pwd
                    ls
                    date
                    cat'''
            }
        }

        stage("D") {
            steps {
                echo "========executing A========"
            }
        }
    }
    post {
        always {
            echo "========always========"
        }
        success {
            script {
                echo "========pipeline executed successfully ========"
                echo "User who pushed changes: ${BUILD_USER}"
            }
        }
        failure {
            script {
                echo "========pipeline execution failed========"
                echo "User who pushed changes: ${BUILD_USER}"
            }
        }
    }
}
