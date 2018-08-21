pipeline {
    agent any

    stages {
        stage('Build Application') {
            steps {
                withMaven(maven: 'M3') {
                    sh "mvn package -DskipTests"
                }
            }
        }
        stage('Build Container Image') {
            steps {
                withMaven(maven: 'M3') {
                    sh "mvn dockerfile:build dockerfile:tag@version"
                }
            }
        }
        stage('Push Image to Registry') {
            steps {
                withMaven(maven: 'M3') {
                    sh "mvn dockerfile:push dockerfile:push@version"
                }
            }
        }
    }
}
