def DOCKER_HUB_USER="pkw0301"
def DOCKER_IMAGE_NAME="my-tomcat-app"
def DOCKER_IMAGE_TAG="1.0.0"
def DOCKER_CONTAINER_NAME="my-app"
def JOB_NAME="docker-deploy"



node {
  stage('Git Checkout') {
        git url: 'https://github.com/prakashk0301/maven-project.git',
          branch:'ci-cd-with-docker'
  }
  
  stage('Maven Package') {
      def MAVEN_HOME  = tool 'LocalMaven'
      sh "${MAVEN_HOME}/bin/mvn clean package"
   }
	
  stage('Build Docker Image'){
//	  sh 'docker build /var/lib/jenkins/workspace/docker-deploy/ -t ${DOCKER_HUB_USER}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}'
//	  sh 'cd /var/lib/jenkins/workspace/${JOB_NAME}'
	  imageBuild(DOCKER_HUB_USER, DOCKER_IMAGE_NAME, DOCKER_IMAGE_TAG)
   }

  stage('Upload Image to DockerHub'){
    withCredentials([usernamePassword(credentialsId: 'dockerHubAccount', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
		// some block
		sh "docker login -u ${DOCKER_HUB_USER} -p ${dockerHubAccount}"
		}

		sh 'docker push ${DOCKER_HUB_USER}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}'
  }
  
  stage('Remove Old Container my-app'){
    sshagent(['docker-instance-dev']) {
      try{
        def sshCmd = 'ssh -o StrictHostKeyChecking=no ec2-user@172.31.39.173'
        def dockerRM = 'docker rm -f ${DOCKER_CONTAINER_NAME}'
        sh "${sshCmd} ${dockerRM}"
      }catch(error){

      }
    }
  }
  stage('deploy-docker-container-to-dev-env'){
    sshagent(['docker-instance-dev']) {
      //input 'docker-instance-dev?'
      def sshCmd = 'ssh -o StrictHostKeyChecking=no ec2-user@172.31.39.173'
      def dockerRun = 'docker run -d -p 8080:8080 --name ${DOCKER_CONTAINER_NAME} ${DOCKER_HUB_USER}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}'
      sh "${sshCmd} ${dockerRun}"
    }
  }
}
