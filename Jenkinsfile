def gv

pipeline {
    agent any
    parameters {
        choice(name: 'VERSIONS', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Versions available')
        booleanParam(name: 'executeTests',  defaultValue: true, description: '')
    }
    
    stages {
        stage("init") {
            steps {
             script {
                gv = load "script.groovy"
             }
            }
        }

        stage("Build") {
            steps {
                script {
                    gv.buildApp
                }
            }
        }

        stage("Test") {
            when {
                expression {
                    params.executeTests == true
                }

            steps {
               script {
                    gv.testApp
                }
               }
            }
        
        stage("Deploy") {
            steps {
               script {
                    gv.deployApp
                }
            }
        }
    }
}
}
