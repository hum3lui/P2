pipeline {
    agent any
    parameters {
        string(name: 'Target', defaultValue: 'Jenkins', description: 'Who should I say hello to?')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building in ${Target} ..."
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                bat 'javac helloWorld.java'
                bat 'java helloWorld'
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