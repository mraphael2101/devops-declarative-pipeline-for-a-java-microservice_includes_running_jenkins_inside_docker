

// A DECLARATIVE PIPELINE

pipeline {
	// All subsequent steps will now happen inside a docker container
	agent any
	// Figure out why you cannot run jenkins inside a docker container
	//agent{ docker { image 'maven:3.8.4-adoptopenjdk-11' } }
	
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	
	stages {
		stage('Build') {
			steps {
				// Example shell script in the groovy file
				// sh 'mvn --version'
				// sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
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
