pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('build && SonarQube analysis') {
            steps {
		        withSonarQubeEnv('sonar') {
                    withMaven(maven : 'Local_Maven') {
                        sh 'mvn clean install sonar:sonar'
                }
            }
        }

         
}
}
