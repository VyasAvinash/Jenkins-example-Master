pipeline {
	environment {
		SRC="SRC"
		AB="AB"
		CD="CD"
		TEMP="temp"
	}
	options {
		buildDiscarder(logRotator(daysToKeepStr : '10', numToKeepStr: '10')) 
		//skipDefaultCheckout() 
	}
  agent any
  stages {
	  stage('checkout') {
      steps {
	     	// bat "cocolic --license-server=srv-license1.lios-koeln.de:49344 --check"
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '4bda2a04-20c7-470d-ba65-2d8eed7dbbba', url: 'https://github.com/VyasAvinash/Jenkins-example-Master.git']]])
	 }
    }
	  stage("coverage report") {
	  steps {
		  bat "cd ${SRC}\\${AB}_${CD}\\${TEMP}\a.bat"
		
	  }
    }
	  	
  }
}
