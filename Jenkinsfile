@Library("jenkins-shared-libraries") _

pipeline {
    agent any

    environment {
        dockerImage = ''
        MAVEN_OPTS = '-Djansi.force=true'
    }

    tools { 
        maven 'maven'
        gradle 'gradle'
        jdk 'jdk' 
    }

    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        ansiColor('xterm')
    }

    stages {
            stage('Sonarqube') {
                steps {
                    sh """
                      ./gradlew sonarqube \
                      -Dsonar.projectKey=sa-backend \
                      -Dsonar.host.url=http://34.87.28.55:9000 \
                      -Dsonar.login=27bfe3795a57814066782c86f6d6ae032bece0c9
                    """
                }
            }
        }
}
