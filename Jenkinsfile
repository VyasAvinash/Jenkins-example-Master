pipeline {
    agent master

    stages {
	  
	stage ("checkout")
	    {
		  checkout([$class: 'GitSCM', branches: [[name: '*master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout'], [$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false], [$class: 'PruneStaleBranch']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '4bda2a04-20c7-470d-ba65-2d8eed7dbbba', 
		  url: 'https://github.com/VyasAvinash/Jenkins-example-Master.git'']]])  
		    
	    }
	    
	    
	stage("Post build actions") {
            steps {
                junit 'nosetests.xml'
            }
	}
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn deploy'
                }
            }
        }

    }
}
