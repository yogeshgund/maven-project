pipeline {
    agent any


    stages {
        {
        
        stage ('SCM Checkout') {
            steps {
          git 'https://github.com/prakashk0301/maven-project'
         }
        }
    }
        
        stage ('Compile Stage') {
            steps {
                withMaven(maven : 'LocalMaven') 
                {   
                    sh 'mvn compile' 
                }
                }
                  }
                                
            
        
        
        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven')
                {
                    sh 'mvn test'
                }
                  }
                                 
        }

        
        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven')
                {
                    sh 'mvn install'
                }
                                  
                   }
        }

         
}
}
