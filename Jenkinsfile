pipeline {
    agent any
    stages 
    {       
        stage ('SCM Checkout') {
          git 'https://github.com/prakashk0301/maven-project'
         }  
    }
    {
        stage ('parallel execute test') {
            parallel (
                    "unit test" : {
                        build("unit-test-job")
                    },
                    "component test" : {
                        build("component-test-job")
                    }
                )


    }      
  }
}
