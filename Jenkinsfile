pipeline {
	environment {
		BUILD_TYPE = "Coverage"
		BUILD = "Debug"
		CONFIGURATION = "Win64"
		BUILD_FOLDER = "_w64c"
		DEBUG_COVERAGE = "_build\\bin\\${CONFIGURATION}\\${BUILD}_${BUILD_TYPE}"
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
		  dir("${src}/${AB}_${CD}"){
			  publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'simple.html', reportName: 'Coverage report', reportTitles: ''])
		  }
		  
		  bat "echo  ${env.DEBUG_COVERAGE}"
		  bat "cd ${SRC}\\${AB}_${CD}\\${TEMP}\\"
		  load "b.groovy"
		 
	  }
    }
	  	
  }
}
