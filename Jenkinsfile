pipeline{
    agent any

    stages{
        stage('One'){
            steps {
                echo "In in stage one"
            }
        }

        stage('Two'){
            steps {
                echo "Im in stage two"
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