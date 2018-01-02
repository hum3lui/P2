pipeline {
    agent any
    parameters {
        string(name: 'Target', defaultValue: 'Jenkins', description: 'Who should I say hello to?')
    }

    stages {
        stage('Build') {
            agent {
                label any
            }
            steps {
                echo "Building in ${Target} ..."
            }
        }
	    stage('grouped_stage'){
		    parallel {
		        stage('Test') { 
		            agent {
		                label any
		            }
		            environment {
		                PATH = "%path%;C:\\Windows\\SysWOW64;C:\\Program Files (x86)\\Java\\jdk1.8.0_151\\bin"
		            }   
		            steps {
		                bat 'javac helloWorld.java'
		                bat 'java helloWorld'
		            }
		        }
		        stage('Deploy') {
		            agent {
		                label any
		            }
		            steps {
		                echo 'Deploying...'
		            }
		        }
		    }
		}
    }


     post {
        success{
            echo '[updated message]'
        }
        failure {
            echo '[rollback process]'
        }
        
    }
}