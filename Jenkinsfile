  pipeline{
  environment {
      dockerimagename = "poonamtandon1/testing"
      dockerImage = ""
    }
  agent any
    tools {
           maven 'maven-3.8.5'
       }
      stages {
               stage ('Compile Stage'){
                  steps {
                    sh 'mvn clean compile'
                  }
                  }
        stage ('Build Stage'){
          steps{
            sh 'mvn clean package'
          }
        }
        stage('Build image') {
              steps{
                script {
                  dockerImage = docker.build dockerimagename
                }
              }
            }
        }
}
