pipeline{
    agent {
        label 'ANSIBLE'
    }

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

    // triggers { cron('H */4 * * 1-5') }
    // triggers { pollSCM('H */4 * * 1-5') }

    tools {
        maven 'maven-381' 
    }

    parameters {
        // string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        // text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        // booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        // password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages{
        stage('One'){
            when {
                environment name: 'CHOICE', value: 'Three'
            }
            steps {
                echo "In in stage one"
                echo "ENV_VAL IS ${ENV_VAL}"
                // sleep 300
                sh '''mvn --version'''
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
                    hostname
                '''
            }
        }
    }
}