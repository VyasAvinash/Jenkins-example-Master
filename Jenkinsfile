#!/usr/bin/env groovy
void sendEmail(String file2) {
	def file = 'scripts/ci/groovy/' + script
	echo file
	load file

}

pipeline {
	options {
		buildDiscarder(logRotator(daysToKeepStr : '10', numToKeepStr: '10')) 
		//skipDefaultCheckout() 
	}
  agent any
  stages {
	  stage('checkout') {
      steps {
        checkout([$class: 'GitSCM', 
        				   branches: [[name: '*master feature/* bug/*']], 
        				   doGenerateSubmoduleConfigurations: false,      				  
        				   userRemoteConfigs: [[credentialsId: '4bda2a04-20c7-470d-ba65-2d8eed7dbbba', url: 'https://github.com/VyasAvinash/Jenkins-example-Master.git']]])
	script {
	     sendEmail(b.groovy)
	 }
      }
    }
	  	
  }
  
  parameters {
    	string(name: 'NAME', defaultValue: 'release/4.2.20.X', description: '')
  }
}
