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
//agent any
	agent {docker {image 'maven:3.6.3'}}
	stages{
		stage('Build'){
			steps{
				sh 'maven --version'
				echo "build"

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
