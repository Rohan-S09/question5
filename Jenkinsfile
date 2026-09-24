pipeline {
    agent any
 
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
 
        stage('Parallel Checks') {
            parallel {
                stage('Unit Check') {
                    steps {
                        bat 'python unit_check.py'
                    }
                }
                stage('Integration Check') {
                    steps {
                        bat 'python integration_check.py'
                    }
                }
            }
        }
 
        stage('Summary') {
            steps {
                echo 'Summary: unit_check and integration_check both completed.'
            }
        }
    }
 
    post {
        success {
            echo 'SUCCESS: All checks passed.'
        }
        failure {
            echo 'FAILURE: A check failed. Pipeline stopped.'
        }
    }
}
