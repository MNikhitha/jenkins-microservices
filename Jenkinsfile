//SCRIPTED
//node {

	// stage('Build') {
	// 	echo "Build"
	// }
	// stage('Test') {
	// 	echo "Test"
	// }
	// stage('Integration Test') {
	// 	echo "Test"
	// }}
//DECLARATIVE
pipeline{
agent any
	//agent {docker {image 'maven:3.8.4'}}
	//agent {docker {image 'node:13.8'}}
	environment{
		dockerHome = tool 'MyDocker'
		mavenHome = tool 'MyMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin"

	}
	stages{
		stage('Build'){
			steps{
				sh 'maven --version'
				sh 'docker version'
				echo "build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"

			}
		}
		stage('Deploy'){
			steps{
				echo "Deploy"

			}
		}
		stage('Test'){
			steps{
				echo "test"

			}
		}
	}
	//changed,unstable
	post{
		always{
			echo 'successful'
		}
		success{
			echo 'success'
		}
		failure{
			echo 'failed'
		}
	}
}
