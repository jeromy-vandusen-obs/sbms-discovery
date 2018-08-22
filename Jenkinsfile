pipeline {
    agent any

    stages {
        stage('Run Unit Tests') {
            steps {
                withMaven(maven: 'M3') {
                    sh "mvn clean test"
                }
            }
            post {
                always {
                    junit "target/surefire-reports/*.xml"
                }
            }
        }
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
                    sh "mvn dockerfile:build dockerfile:tag@version -DskipTests"
                }
            }
        }
        stage('Push Image to Registry') {
            steps {
                withMaven(maven: 'M3') {
                    sh "mvn dockerfile:push dockerfile:push@version -DskipTests"
                }
            }
        }
    }
}
