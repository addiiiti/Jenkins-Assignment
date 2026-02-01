pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Main Branch Tests') {
            when {
                branch 'main'
            }
            steps {
                echo "Running tests on main branch"
            }
        }

        stage('Feature Branch Validation') {
            when {
                expression { env.BRANCH_NAME.startsWith('feature') }
            }
            steps {
                echo "Running feature branch checks"
            }
        }
    }
}
