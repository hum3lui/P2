#!/usr/bin/env groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                def target = 'Jenkins'
                echo "Building in ${target} ..."
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }

     post {
        success{
            echo 'updated message'
        }
        failure {
            echo 'rollback process'
        }
        
    }
}