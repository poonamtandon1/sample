  pipeline{
     agent any
      stages {
               stage ('Compile Stage'){
                   steps {
                    withMaven(maven: 'M3') {
                         sh "mvn clean install "
                     }
                    }
               }
      }
  }
