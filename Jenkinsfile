pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                withMaven(maven: 'M3') {
                    sh "mvn clean package dockerfile:build dockerfile:tag@version dockerfile:push dockerfile:push@version"
                }
            }
        }
    }
}
