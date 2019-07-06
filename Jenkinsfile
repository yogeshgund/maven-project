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
            if {
                branch 'when-condition-ci-cd'
            }
            steps {
                withMaven(maven : 'LocalMaven') 
                {   
                    sh 'mvn compile' 
                }
                else {
                    echo 'skip'
                }
                  }

            }
         }
    }      
  }
