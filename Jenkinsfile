pipeline {
    agent any
	
	
	stages
	{
	
	stage "SCM Checkout" {
	git 'https://github.com/yogeshgund/maven-project.git'
	}
	}
	{
		
	
	stage ('testing stage') {
		
	steps {
	     withMaven(maven: 'LocalMaven') 
		 {
	      sh 'mvn test'
         }
    }
    }
}
}
