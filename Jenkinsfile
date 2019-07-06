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
                branch 'master'
            }
            steps {
                withMaven(maven : 'LocalMaven') 
                {   
                    sh 'mvn compile' 
                }
                }
                  }
        stage ('skip compiled stage') {
            when {
                not {
                    branch 'master'
                }
            }
            steps {
            echo "skipping job"
            }
         }
    }      
  }
