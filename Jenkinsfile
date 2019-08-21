#!/usr/bin/env groovy

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
	      currentBuild.result = "FAILURE"
	 }
      }
	post {
		failure {
			script {
			 	echo "checkout failed"
				 //currentBuild.result = "FAILURE"
				// error "checkout error thrown"
				echo "$currentBuild.result"
			}
		}	
		success {
			echo "checkout success"
		  }
	
   	 }
    }
	  
    stage ('deploy') {
	    steps {
		script {
			if (currentBuild.result == "SUCCESS") {
	 			
					echo 'deployment stage' 
					load 'b.groovy'
			}
		}
   	    }
	 post { 

		failure {
			  echo "Post : Deploy Failed!"
			}
	 }

     }
	
  }
  
  parameters {
    	string(name: 'NAME', defaultValue: 'release/4.2.20.X', description: '')
  }
}
