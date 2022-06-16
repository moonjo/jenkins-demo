def gv

pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: '')
    }
    stages {
        
        stage('Init') {
            steps {
                script {
                    gv = load "myscript.groovy"
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    gv.buildApp()
                }
            }
        }
        stage('Test') {
            when {
                expression {
                    params.RUN_TESTS
                }
            }
            steps {
                script {
                    gv.testApp()
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing'
            }
        }
    }
}
