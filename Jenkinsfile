#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
         stage('Setup') {
            steps {
                git url:'http://10.250.10.2:8929/root/hello-grails.git', branch: 'main'
            }
        }

        stage('Test') {
            steps {
                withGradle {
                    sh './gradlew test'
                    sh './gradlew test jacocoTestReport'
                }
            }
            post {
                always {
                    junit 'build/test-results/test/TEST-*.xml'
                }
            }
        } 
        
    }
}
