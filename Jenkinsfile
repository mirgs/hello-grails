#!/usr/bin/env groovy
pipeline {
    agent any
    /*tools {
        jdk 'OpenJDK-15.0.2'
    }*/



    stages {
         stage('Setup') {
            steps {
                git url:'http://10.250.10.2:8929/root/hello-grails.git', branch: 'master'
            }
        } 

        /*stage('Build') {
            steps {
                withGradle {
                    sh './gradlew bootRun'
                }
            }
            post {
                success {
                    archiveArtifacts 'build/libs/*.jar'
                }
            }
        }*/

        stage('Test') {
            steps {
                withGradle {
                    sh './gradlew clean test'
                    sh './gradlew -Dgeb.env=firefoxHeadless iT'
                    /*sh './gradlew test jacocoTestReport'*/
                }
            }
            post {
                always {
                    junit 'build/test-results/test/TEST-*.xml'
                }
            }
        } 

        /*stage('Test-Integration') {
            steps {
                withGradle {
                    sh './gradlew clean integrationTest'
                    sh './gradlew integrationTest jacocoTestReport'
                }
            }
            post {
                always {
                    junit 'build/test-results/integrationTest$/TEST-*.xml'
                }
            }
        }*/
        
    }
}
