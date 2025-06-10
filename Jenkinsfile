pipeline {
    agent any

    tools {
        maven 'Maven' // Make sure 'Maven' is the correct tool name configured in Jenkins (Manage Jenkins > Global Tool Configuration)
        // Optionally: jdk 'Java' // if you're using a named JDK tool
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/prajwalfm05/MyMaven.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package' // Runs Maven build
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test' // Runs unit tests
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -jar target/MyMaven-1.0-SNAPSHOT.jar' // Make sure the jar name is correct and built by Maven
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
