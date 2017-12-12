pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                def Target = 'Jenkins'
                echo 'Building in ${Target} ...'
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