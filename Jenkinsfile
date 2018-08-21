pipeline {
    agent any

    stages {
        stage('Build Application') {
            steps {
                withMaven() {
                    sh "mvn package -DskipTests"
                }
            }
        }
        stage('Build Container Image') {
            steps {
                withMaven() {
                    sh "mvn dockerfile:build dockerfile:tag@version"
                }
            }
        }
        stage('Push Image to Registry') {
            steps {
                withMaven() {
                    sh "mvn dockerfile:push dockerfile:push@version"
                }
            }
        }
    }
}
