pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
            }
        }
    }

    post {
        success {
            script {
                // Print information about the GitHub push event
                echo "GitHub Push Event:"
                echo "  ID: ${CHANGE_ID}"
                echo "  URL: ${CHANGE_URL}"
                echo "  Title: ${CHANGE_TITLE}"
                echo "  Author: ${CHANGE_AUTHOR}"
            }
        }
    }
}
