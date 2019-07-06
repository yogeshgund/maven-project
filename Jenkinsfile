pipeline {
    agent any
    stages 
    {       
        stage ('SCM Checkout') {
          git 'https://github.com/prakashk0301/maven-project'
         }  
    }
    {
        stage ('Compile Stage') {
            when {
                branch 'when-condition-ci-cd'
            }
            steps {
                withMaven(maven : 'LocalMaven') 
                {   
                    sh 'mvn compile' 
                }
                }
                  }
        stage ('test stage when branch is pipeline-demo2') {
            when {
                not {
                    branch 'pipeline-demo2'
                }
            }
            steps {
                withMaven(maven : 'LocalMaven')  
                {   
                      sh 'mvn test' 
            }
         }
    }      
  }
