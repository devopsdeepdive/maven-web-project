pipeline {
	agent any
stages {
        stage('Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/batch17']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_credentials', url: 'https://github.com/devopsdeepdive/maven-web-project.git']]]) 
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
		stage('Package') { 
            steps {
              sh 'mvn package'
            }
        }
	
	stage('Deploy'){
	steps{
		sshagent(['deploy']) {
			sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven-web-project/target/*.war ubuntu@ec2-54-198-135-17.compute-1.amazonaws.com://opt/tomcat/webapps/'
		}
	}
}
	}
}
