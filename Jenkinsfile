pipeline{
    agent any
    stages{
        stage("Echo a line"){
            steps{
                echo 'This is step one'
            }
        }

        stage("Run a command"){
            steps{
                sh 'pwd'
            }
        }

        stage("Run multiple commands"){
            steps{
                sh '''pwd
                    ls
                    date
                    cat'''
            }
        }

       stage("D"){
            steps{
                echo "========executing A========"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
