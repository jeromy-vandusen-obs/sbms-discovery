node {
    stage('Run Unit Tests') {
        withMaven(maven: 'M3') {
            sh "mvn clean test"
        }
    }
    stage('Build Application') {
        withMaven(maven: 'M3') {
            sh "mvn package -DskipTests"
        }
    }
    stage('Build Container Image') {
        withMaven(maven: 'M3') {
            sh "mvn dockerfile:build dockerfile:tag@version -DskipTests"
        }
    }
    stage('Push Image to Registry') {
        withMaven(maven: 'M3') {
            sh "mvn dockerfile:push dockerfile:push@version -DskipTests"
        }
    }
}
