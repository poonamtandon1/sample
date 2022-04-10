  pipeline{
  environment {
      dockerimagename = "poonamtandon1/testing"
      dockerImage = ""
    }
  agent {
           docker {
               image 'maven:3.8.1-adoptopenjdk-11'
               args '-v /root/.m2:/root/.m2'
           }
       }
      stages {
               stage ('Compile Stage'){
                  steps {
                    sh 'mvn clean compile'
                  }
                  }
        stage ('Build Stage'){
          steps{
            sh 'mvn clean install'
            script {
            dockerImage = docker.build dockerimagename
            }
            }



        }
        }
}
