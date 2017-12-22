pipeline {
    agent none
    parameters {
        string(name: 'Target', defaultValue: 'Jenkins', description: 'Who should I say hello to?')
    }

    stages {
        stage('Build') {
            agent {
                label "windows"
            }
            steps {
                echo "Building in ${Target} ..."
            }
        }
        stage('Test') { 
            agent {
                label "windows"
            }
            environment {
                PATH = "%path%;C:\\Windows\\SysWOW64;C:\\Program Files (x86)\\Java\\jdk1.8.0_151\\bin"
            }   
            steps {
                parallel(
                    a: {
                        bat 'javac helloWorld.java'
                        bat 'java helloWorld'
                    },
                    b: {
                        echo 'it is branch b'
                    }
                )
            }
        }
        stage('Deploy') {
            agent {
                label "windows"
            }
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