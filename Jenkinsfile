pipeline{
    agent any

    environment {               // Pipeline variables
        ENV_VAL = "pipeline.google.com"
    }

    stages{
        stage('One'){
            steps {
                echo "In in stage one"
                echo "ENV_VAL IS ${ENV_VAL}"
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
                sh '''echo Hello World
                    echo Hai World
                    echo I am using pipeline syntax generator
                '''
            }
        }
    }
}