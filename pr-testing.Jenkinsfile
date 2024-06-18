pipeline {
    agent any

    stages {
        stage('Unittest') {
            steps {
                bat 'echo "testing"'
            }
        }
        stage('Lint') {
            steps {
                bat 'python3 -m pylint -f parseable --reports=no *.py > pylint.log'
            }
            post {
                always {
                    bat 'cat pylint.log'
                    recordIssues (
                        enabledForFailure: true,
                        aggregatingResults: true,
                        tools: [pyLint(name: 'Pylint', pattern: '**/pylint.log')]
                    )
                }
            }
        }
        stage('Functional test') {
            steps {
                bat 'echo "testing"'
            }
        }
    }
}