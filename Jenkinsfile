node{
    stage ('scm checkout') {
	git ('https://github.com/prakashk0301/maven-project')
	}
	
	stage('Checkout to different branch') {
        sh "git branch -r"
        sh "git checkout ci-cd-with-docker"
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
	
       stage('Remove Old Containers'){
           sshagent(['deploy-to-dev-docker']) {
             try{
               def sshCmd = 'ssh -o StrictHostKeyChecking=no ec2-user@172.31.46.1'
               def dockerRM = 'docker rm -f my-tomcat-app'
                 sh "${sshCmd} ${dockerRM}"
                 }catch(error){

      }
    }
  }
	
	
	

       stage ('Deploy to Dev') {
	   def dockerRun = 'docker run -d -p 9000:8080 --name my-tomcat-app pkw0301/my-app:1.0.0'
	   sshagent(['deploy-to-dev-docker']) {
             sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.46.1 ${dockerRun}"
   }
  }	
}





	
	
