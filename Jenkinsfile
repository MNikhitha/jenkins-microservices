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
		stage('Checkout'){
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
		stage('Compile'){
			steps{
				sh 'mvn clean compile'

			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
			
		}
		stage('Integration test'){
			steps{
				sh "mvn failsafe:integration-test  failsafe:verify"
			}

		}
		stage('package'){
			steps{
				sh "mvn package -DskipTests"
			}

		}
		stage('Build docker image'){
			steps{
                //"docker build -t nikhi28/jenkins-microservices-pipeline:$env.BUILD_TAG"
		        script{
					dockerImage=docker.build("nikhi28/jenkins-microservices-pipeline:${env.BUILD_TAG}")
				}
			}
		
		}
		stage('Push docker image'){
			steps{
				script{
					docker.withRegistry('','dockerhubcre'){
						dockerImage.push();
						dockerImage.push('latest')
					}
				}
				
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
