  pipeline{
 
  agent any
      stages {
               stage ('Compile Stage'){
                   withMaven {
                  steps {
                    sh 'mvn clean compile'
                  }
                  }
               }
      }
  }
