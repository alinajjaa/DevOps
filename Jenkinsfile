pipeline {
    agent any

    // Tools installed in Jenkins
    tools {
        jdk 'JDK 21'       // Change to the name of your JDK installation in Jenkins
        maven 'M3'         // Name of the Maven installation you created
    }

    environment {
        MAVEN_OPTS = "-Xmx1024m"
    }

    stages {

        stage('Checkout') {
            steps {
                // Pull code from Git
                git branch: 'main', url: 'https://github.com/alinajjaa/DevOps.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean compile'   // Compile only first
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
            post {
                always {
                    // Publish JUnit test results
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the project...'
                sh 'mvn package'         // Create jar/war file
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage placeholder'
                // Add deploy commands if needed
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs above.'
        }
    }
}
