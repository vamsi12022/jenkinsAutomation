pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Example: Archive the generated JAR/WAR file
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                // In a real-world scenario, this stage would involve:
                // - Pushing to an artifact repository (e.g., Nexus, Artifactory)
                //   sh 'mvn deploy' // Requires distributionManagement in pom.xml
                // - Deploying to a server (e.g., using SSH, Ansible, Kubernetes tools)
                //   sh 'scp target/my-app.jar user@remote-server:/path/to/deploy'
                //   script {
                //       // Example for a more complex deployment
                //       // sh "kubectl apply -f k8s/deployment.yaml"
                //   }
            }
        }
    }
    post {
        always {
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