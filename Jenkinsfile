pipeline {
    agent any

    tools {
        maven 'M3'  // Must match the name in Global Tool Configuration
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
