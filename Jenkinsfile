pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    options {
        disableConcurrentBuilds()
    }

    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Test & Build') {
            steps {
                sh 'chmod +x gradlew && ./gradlew clean test bootJar'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build/libs/app.jar', fingerprint: true
            }
        }
    }
}