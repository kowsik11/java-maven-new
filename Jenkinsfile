pipeline {
    agent any
    tools {
        maven 'maven3'
        jdk 'jdk21'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Archive Artifact & Reports') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                archiveArtifacts artifacts: 'target/surefire-reports/*.xml'
            }
        }
    }
}
