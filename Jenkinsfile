pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'make build'
                echo "Started by Github push by ${GIT_PUSHER_NAME}"
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
