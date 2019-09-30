#!/usr/bin/env groovy
void sendEmail(String file2) {
	def file = 'scripts/ci/groovy/' + file2
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
		scm checkout	
	 }
      }
	  stage("coverage report") {
		  bat "cd src"
		// 1.First merge csmes files 	(2) Combine csmes, csexe files	(3) Publish report into html format	(4) Creates a file report.html and a directory report_html
		bat """cmmerge -o output.csmes *.csmes
		cmcsexeimport  -m output.csmes -t Execution -e Charon4IntegrationTests.exe.csexe -e Charon4UnitTests.exe.csexe
		cmreport -m output.csmes --html=report
		"""
		publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'report.html', reportName: 'Coverage report', reportTitles: ''])
	  }
    }
	  	
  }
  
  parameters {
    	string(name: 'NAME', defaultValue: 'release/4.2.20.X', description: '')
  }
}
