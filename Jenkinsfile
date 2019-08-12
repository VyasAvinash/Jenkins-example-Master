pipeline {
	options {
		buildDiscarder(logRotator(daysToKeepStr : '10', numToKeepStr: '10')) 
	}
  agent any
  stages {
    stage('checkout') {
      steps {
        checkout([$class: 'GitSCM', 
        				   branches: [[name: '*master feature/*']], 
        				   doGenerateSubmoduleConfigurations: false, 
        				   extensions: [[$class: 'CleanBeforeCheckout'], [$class: 'CloneOption', depth: 2, noTags: false, reference: '', shallow: false], [$class: 'PruneStaleBranch']],
        				   userRemoteConfigs: [[credentialsId: '4bda2a04-20c7-470d-ba65-2d8eed7dbbba', url: 'https://github.com/VyasAvinash/Jenkins-example-Master.git']]])
      }
    }
  }
  parameters {
    	string(name: 'NAME', defaultValue: 'release/4.2.20.X', description: '')
  }
}
