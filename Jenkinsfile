pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Started by Github push by ${CHANGE_AUTHOR}"
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

