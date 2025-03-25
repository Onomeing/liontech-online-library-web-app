pipeline{
	agent any
	tools{
		maven "maven3.9.9"
	}

	stages{
		stage('clone from scm'){
			steps{
				sh "echo jenkins to clone from scm"
				git branch: 'march24', url: 'https://github.com/Onomeing/liontech-online-library-web-app.git'

			}
		}

		stage('maven build'){
			steps{
				sh " echo 'running junit test on the source code'"
				sh "echo 'maven to build and package the source code'"
				sh "mvn install"
				sh "mvn verify"
				sh "mvn test"
				sh "mvn validate"
				sh "mvn clean package"
			}
		}
	}
}
