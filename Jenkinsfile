pipeline {
    agent any

    environment {
        BRANCH = 'main'
    }

    stages {
        stage('Check Pull Request') {
            when {
                expression {
                    return env.CHANGE_ID && env.CHANGE_TARGET == env.BRANCH
                }
            }
            steps {
                echo "Running PR #${env.CHANGE_ID} targeting ${env.CHANGE_TARGET}"
            }
        }

        stage('Deploy') {
            when {
                expression {
                    return env.CHANGE_ID && env.CHANGE_TARGET == env.BRANCH
                }
            }
            steps {
                sh 'echo "Deploying..."'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
