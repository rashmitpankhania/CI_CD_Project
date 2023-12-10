#!/usr/bin/env groovy
pipeline {

    agent any
    triggers {
        pollSCM 'H/15 * * * *'
    }
    tools {
        maven 'Maven-3.6.3'
    }
    options {
        timeout(60)
        timestamps()
    }
    stages {
        stage('Compile Junit') {
            steps {
                script {
                    CURRENT_STAGE = env.STAGE_NAME
                }

                catchError(buildResult: 'SUCCESS') {
                    script {
                        sh "'mvn' clean compile test integration-test"
                    }
                }
            }
        }
        stage('Package') {
            steps {
                script {
                    CURRENT_STAGE = env.STAGE_NAME
                }

                catchError(buildResult: 'SUCCESS') {
                    script {
                        sh "'mvn' package"
                    }
                }
            }
        }
        stage('Collect Aritifacts') {
            steps {
                script {
                    CURRENT_STAGE = env.STAGE_NAME
                }

                script {
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
        post {
            always {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}