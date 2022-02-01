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
	stages{
		stage('Build'){
			steps{
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
