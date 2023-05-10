pipeline {
	agent any
stages {
        stage('Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/batch15']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_cred', url: 'https://github.com/devopsdeepdive/maven-web-project.git']]]) 
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
	
	stage('Deploy') { 
            steps {
             sshagent(['tomcat_server']) {
		sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven-web-project/target/maven-web-application.war ubuntu@172.31.21.31:/opt/tomcat/apache-tomcat-9.0.74/webapps'   
            }
        }
	}
	}
}
