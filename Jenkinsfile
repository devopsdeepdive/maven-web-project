pipeline {
	agent any
stages {
        stage('Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/anurag']], extensions: [], userRemoteConfigs: [[credentialsId: 'GITHUB_AUTH', url: 'https://github.com/devopsdeepdive/maven-web-project.git']]]) 
            }
        }
	}
}
