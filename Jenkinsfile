pipeline {
    agent any
    stages 
    {       
        stage ('SCM Checkout') {
          git 'https://github.com/prakashk0301/maven-project'
         }  
    }
    stage ("parallel tests") {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                    sh 'mvn test'
                    } 
                     
             
                    
                }
                   

            }
        }
}
