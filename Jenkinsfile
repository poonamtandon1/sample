  pipeline{
    tools {
        maven 'apache-maven-3.0.1' 
    }
     agent any
      stages {
               stage ('Compile Stage'){
                   steps {
                      sh "mvn clean install "
                     
                    }
               }
      }
  }
