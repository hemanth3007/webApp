pipeline {
	agent any
	tools {
		maven 'maven'
	}
	stages {
		stage('Checkout') {
			steps {
				git branch: 'main', url: 'https://github.com/hemanth3007/webApp.git'
			}
		}
		stage('Compile') {
			steps {
				sh 'mvn compile'
			}
		}
		stage('Package') {
			steps {
				sh 'mvn package'
			}
		}
		stage('Run Application') {
			steps {
				sudo sh 'ansible-playbook deploy.yml'
			}
		}
	}
	post {
		success {
			echo 'Build successful'
		}
		failure {
			echo 'Build failure'
		}
	}
}
