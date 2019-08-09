pipeline {
    agent any
   parameters {
		string(name: 'NAME', defaultValue: "release/4.2.20.X", description: '')
   }
    stages {
	  
	    stage ("checkout") {
	   	steps  {
		  checkout scm : [$class: 'GitSCM', 
				   branches: [[name: '*master']], 
				   doGenerateSubmoduleConfigurations: false, 
				   extensions: scm.extensions + [[$class: 'CleanBeforeCheckout'], 
				[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false], 
				[$class: 'PruneStaleBranch']]]
		}
	    }
	    
	    


    }
}
