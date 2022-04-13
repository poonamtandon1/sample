  pipeline{
    agent any
    tools {
        maven 'maven-3.8.5' 
    }
    
      stages {
               stage ('Compile Stage'){
                   steps {
                      sh "mvn clean install "
                     
                    }
               }
      }
  }
