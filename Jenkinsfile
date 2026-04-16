pipeline {
  agent any

  tools {
    maven 'Maven3'
    jdk 'JDK21'
  }

  enviroment {
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
  }
}
