pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/shastry-git/Devops-01.git'
        BRANCH = 'main'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: "${BRANCH}", url: "${REPO_URL}"
            }
        }

        stage('Run Python Script') {
            steps {
                bat '''
                python add.py > output.txt
                '''
            }
        }

        stage('Archive Output') {
            steps {
                archiveArtifacts artifacts: 'output.txt', fingerprint: true
            }
        }
    }
}
