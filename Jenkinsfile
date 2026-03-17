pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/shastry-git/Devops-01.git'
        BRANCH = 'main'
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Cloning repo...'
                git branch: "${BRANCH}", url: "${REPO_URL}"
            }
        }

        stage('Run Python Script') {
            steps {
                echo 'Running add.py...'
                sh '''
                python3 add.py > output.txt
                '''
            }
        }

        stage('Archive Output') {
            steps {
                echo 'Archiving output...'
                archiveArtifacts artifacts: 'output.txt', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully ✅'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}
