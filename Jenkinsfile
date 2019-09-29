pipeline {
    agent any
	{	
	
	stages
	{
	
	stage "SCM Checkout" {
	git 'https://github.com/yogeshgund/maven-project.git'
	}
	}
	{
		
	
	stage ('testing stage') {
		
	steps {
	     withMaven(maven: 'localmaven') 
		 {
	      sh 'mvn install'
         }
    }
    }
}
	stage ('deploy to tomcat') {

steps{
  sshagent (['172.31.35.118']) {
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.35.118:/var/lib/tomcat/webapps'
  }
}
	}
}
}
