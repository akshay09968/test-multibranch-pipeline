pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout([$class: 'GitSCM', branches: [[name: '*/main'], [name: '*/dev'], [name: '*/staging'], [name: '*/prod']], userRemoteConfigs: [[url: 'https://github.com/akshay09968/test-multibranch-pipeline.git', credentialsId: 'github']]])
                }
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
}

triggers {
    githubPush(branchFilter: 'main, dev, staging, prod')
}
