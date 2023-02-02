pipeline {
    agent any
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSIONS', choices: ['1.1.0,', '1.2.0', '1.3.0'], description: 'Versions available')
        booleanParam(name: 'executeTests',  defaultValue: true, decription: '')
    }
    }

    stages {
        stage('Build') {
            steps {
               echo 'Building the application'
            }
        }

        stage('Test') {
            when {
                expression {
                    params.executeTests == true
                }

            steps {
               echo 'Testing the application'
               }
            }
        }

        stage('Deploy') {
            steps {
               echo 'Deploying the application'
               echo "Deploying Version ${params.VERSIONS}"
            }
        }
    }
}












