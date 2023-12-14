pipeline {
    agent any

    stages {
        stage('Fetch push event details') {
            steps {
                script {
                    // Get the GitHub API token from Jenkins credentials
                    def token = credentials['github-token'].token

                    // Get the commit SHA from the environment variable
                    def commitSha = env.GIT_SHA

                    // Build the API URL
                    def url = "https://api.github.com/repos/${env.GIT_REPO_OWNER}/${env.GIT_REPO_NAME}/commits/${commitSha}"

                    // Send a GET request to the API
                    def response = sh(
                        command: "curl -X GET -H 'Authorization: token ${token}' ${url}",
                        returnStdout: true
                    )

                    // Parse the JSON response
                    def json = new groovy.json.JsonSlurper().parseText(response)

                    // Extract the user's name from the "committer" object
                    def userName = json.commit.committer.login

                    // Display the user's name below the build number
                    echo "Pushed by: ${userName}"
                }
            }
        }
    }
}
