pipeline {
    agent any

    stages {
        stage('Compile Stage') {
            steps {
                sh 'gradle bootRun'
            }
        }
        stage('Build Stage') {
            steps {
                sh 'gradle clean'
            }
            steps {
                sh 'gradle fatJar'
            }
        }
    }
}