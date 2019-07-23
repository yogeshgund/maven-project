node{
    stage ('scm checkout') {
	git ('https://github.com/prakashk0301/my-app')
	}
	
	stage ('package stage') {
       sh label: '', script: 'mvn clean package '
        }
	stage ('docker image build') {
	   sh 'docker build -t pkw0301/my-app:1.0.0 .'
	
	}
	
	stage ('Push Docker image to DockerHub') {
	  withCredentials([string(credentialsId: 'dockerhubaccount', variable: 'dockerhubaccount')]) {
	     sh "docker login -u pkw0301 -p ${dockerhubaccount}"
	     }
	     sh 'docker push pkw0301/my-app:1.0.0'
	
}	
	
	
	
}





	
	
