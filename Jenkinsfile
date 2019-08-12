
pipeline {
	options {
		buildDiscarder(logRotator(daysToKeepStr : '10', numToKeepStr: '10')) 
	}
  agent any
  stages {
    stage('checkout') {
      steps {
        checkout([$class: 'GitSCM', 
        				   branches: [[name: '*master']], 
        				   doGenerateSubmoduleConfigurations: false, 
        				   extensions: [[$class: 'CleanBeforeCheckout'], 
        				[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false], 
        				[$class: 'PruneStaleBranch']]])
      }
    }
  }
  parameters {
    string(name: 'NAME', defaultValue: 'release/4.2.20.X', description: '')
  }
}
