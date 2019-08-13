def CONTAINER_NAME = "Forge-Template" // Be aware that CONTAINER_NAME cannot contain space, which is not a valid docker container name
env.JENKINS_NODE_COOKIE = 'dontKillMe'

pipeline {
    agent {
        docker {
            image 'openjdk:8u222-jdk-stretch'
            args "--name jenkins-${CONTAINER_NAME}"
        }
    }
    stages {
        stage('Pre-Build') {
            steps {
                sh 'chmod +x gradlew'
            }
        }
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
        }
        cleanup {
            dir('build/libs') {
                deleteDir()
            }
        }
    }
}