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
            environment {
                PATH = "%path%;C:\\Windows\\SysWOW64;C:\\Program Files (x86)\\Java\\jdk1.8.0_151\\bin"
            }   
            steps {
                parallel(
                    a: {
                    agent { label 'windows'}
                    steps{
                        bat 'javac helloWorld.java'
                        bat 'java helloWorld'
                    }
                    },
                    b: {
                    agent { label 'windows'}
                    steps{   
                        echo 'it is branch b'
                    }
                    }
                )
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