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
                parallel ( 
                    withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                    } 
                     
                    withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                    
                }
                   
                )
            }
        }
}
