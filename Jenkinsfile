  pipeline{
 
  agent any
      stages {
               stage ('Compile Stage'){
                   withMaven {
                
                    sh 'mvn clean compile'
                  
                  }
               }
      }
  }
