pipeline 
{
    agent any
	{
	
	stage "SCM Checkout" {
	git 'https://github.com/yogeshgund/maven-project.git'
	}	
	
	stage "code test" 
	{
	     withMaven(maven: LocalMaven') 
		 {
	      sh 'mvn test'
         }
    }
    }
}
