pipeline {
    agent { label 'windows' }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Rohan-S09/question5'
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
                echo 'All checks completed.'
            }
        }
    }
    post {
        success {
            echo 'PIPELINE SUCCESS: all checks passed.'
        }
        failure {
            echo 'PIPELINE FAILED: one or more checks did not pass.'
        }
    }
}
