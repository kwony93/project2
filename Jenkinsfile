pipeline {
  agent any

  tools {
    maven 'Maven3'
    jdk 'JDK21'
  }

  environment {
	  IMAGE_NAME = "hklee2748/spring-petclinic:latest"
  }

  stages {
		stage('check Tools') {
	      steps {
	        dir('spring-petclinic') {
					sh 'mvn -v'
					sh 'docker version'
					sh 'kubectl version --client' 
				}
		  }
		}

		stage('Load Credentials') {
			steps {
				withCredentials([
					file(credentialsID: 'kubeconfig', varialbe: 'KUBECONFIG_FILE'),
					usernamePassword(credentialsID: 'docker-creds', usernameVariable: 'DOCKER_USER')
				]) {
				sh '''
				echo "KUBECONFIG loaded"
				echo "DOCKER user: $DOCKER_USER"
				'''
				}
			}
		}

	
	}
}
