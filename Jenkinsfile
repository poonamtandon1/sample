  pipeline{
  environment {
      dockerimagename = "poonamtandon1/testing"
      dockerImage = ""
    }
  agent any
      stages {
               stage ('Compile Stage'){
                  steps {
                    sh 'mvn clean compile'
                  }
                  }
      }
  }
