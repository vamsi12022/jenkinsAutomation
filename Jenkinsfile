pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                script {
                    echo 'Creating and activating virtual environment...'
                    sh 'python3 -m venv .venv'
                    sh '. .venv/bin/activate && pip install --upgrade pip'
                    echo 'Installing Python dependencies from requirements.txt...'
                    sh '. .venv/bin/activate && pip install -r requirements.txt'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    echo 'Running pytest test suite...'
                    sh '. .venv/bin/activate && pytest'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deployment stage for health checker.'
                echo 'No specific deployment target defined for this example.'
                echo 'Add steps here to deploy your health checker, e.g., to a server, container registry, etc.'
            }
        }
    }

    post {
        always {
            cleanWs()
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}