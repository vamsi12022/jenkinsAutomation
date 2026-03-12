pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add your deployment steps here, e.g.,
                // sh 'scp target/*.jar user@remote:/path/to/app'
                // withMaven(mavenSettingsConfig: 'my-maven-settings') {
                //     sh 'mvn deploy'
                // }
            }
        }
    }
}