pipeline {
	agent {
  	  label 'jenkins-slave'
	}

stages {
        stage('Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/anurag']], extensions: [], userRemoteConfigs: [[credentialsId: 'GITHUB_AUTH', url: 'https://github.com/devopsdeepdive/maven-web-project.git']]]) 
            }
        }
	stage('Build') {
	   steps {
		sh 'mvn compile'
	   }
	}
	stage('Test') {
	   steps {
		sh 'mvn test'
	   }
	}
	stage('Deploy') {
	   steps {
		sh 'echo Deployingprod server.....'
	   }
	}
	}
}
