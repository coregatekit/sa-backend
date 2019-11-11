pipeline {
    agent any

    environment {
        dockerImage = ''
    }

    stages {
        stage('Build') {
            steps {
                sh 'gradlew clean build'
            }
        }
        stage('Test') {
            steps {
                sh 'gradlew test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Build image') {
            steps {
                script {
                    dockerImage = docker.build("coregatekit/sa-backend")
                }
            }
        }
    }
}