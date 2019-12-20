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
                      mvn sonar:sonar \
                      -Dsonar.projectKey=nodejs-hashing \
                      -Dsonar.host.url=http://34.87.28.55:9000 \
                      -Dsonar.login=d2dd6e9da55787554de85b6a120de62c113225d4
                    """
                }
            }
        }
}
