def CONTAINER_NAME = "Forge-Template" // Be aware that CONTAINER_NAME cannot contain space, which is not a valid docker container name

pipeline {
    agent {
        docker {
            image 'openjdk:8u222-jdk-stretch'
            args "--name jenkins-${CONTAINER_NAME}-master"
        }
    }
    environment {
        GRADLE_OPTS = "-Dorg.gradle.daemon=false" // This environment variable aims to disable Gradle Daemon for piles of incompatible Gradle Daemons existence.
    }
    stages {
        stage('Pre-Build') {
            steps {
                sh 'rm -fR build/ .gradle'
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