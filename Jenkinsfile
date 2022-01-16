// A DECLARATIVE PIPELINE

pipeline {
    
	tools {
	    jdk 'myJDK_11'
	}
	
	agent any
	
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	
	stages {
		stage('Build') {
			steps {
			    
			    // Run jenkins inside a docker container
			    script { docker.image ('maven:3.8.4') }
			    
				// Example shell script in the groovy file
				sh 'mvn --version'
				sh 'docker version'
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