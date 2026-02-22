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
        
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        // stage('Archive Artifact & Reports') {
        //     steps {
        //         archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        //         archiveArtifacts artifacts: 'target/surefire-reports/*.xml'
        //     }
        // }
        
        // stage('Deploy') {
        //     steps {
        //         bat 'java -jar target/demo-0.0.1-SNAPSHOT.jar'
        //     }
        // }
    }
}
