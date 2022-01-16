

// A DECLARATIVE PIPELINE

pipeline {
	
	// agent any
	agent { docker { image 'maven:3.6.3' } }	// As a result of this, all subsequent steps will happen inside a docker container

	stages {
		stage('Build') {
			steps {
				sh 'mvn --version' // This is a shell script in the groovy file
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	} 
	post {
		always {
			echo "This block of code will always execute"
		}
		success {
			echo "This block of code only runs if the job is successful"
		}
		failure {
			echo "This block of code only runs if the job fails at a specific step"
		}
	}
}
