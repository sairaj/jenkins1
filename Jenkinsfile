pipeline{
    agent any

    environment {               // Pipeline variables
        ENV_VAL = "pipeline.google.com"
        SSH_CRED = credentials('SSH_CRED')
    }

    options {
        buildDiscarder(logRotator(numToKeepStr: '3'))         // '3' day keep log of only 3 day old builds and discard remaining
        disableConcurrentBuilds()
        disableResume()
        timeout(time: 1, unit: 'MINUTES')
    }

    stages{
        stage('One'){
            steps {
                echo "In in stage one"
                echo "ENV_VAL IS ${ENV_VAL}"
                sleep 300
            }
        }

        stage('Two'){
            environment {               // Pipeline variables
                ENV_VAL = "stage2.google.com"
            }
            steps {
                echo "Im in stage two"
                echo "ENV_VAL IS ${ENV_VAL}"
            }
        }

        stage('Three'){
            steps {
                sh '''
                    echo Hello World
                    echo Hai World
                    echo I am using pipeline syntax generator
                    env
                '''
            }
        }
    }
}