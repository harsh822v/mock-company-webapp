pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Run the Gradle build
                    sh './gradlew assemble'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run the Gradle tests
                    sh './gradlew test'
                }
            }
        }
    }

    post {
        always {
            // Archive test results
            junit '**/build/test-results/test/*.xml'
        }
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}