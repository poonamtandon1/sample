  pipeline{
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
          script {
          dockerImage = docker.build dockerimagename
                 }
               }
   
    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerhublogin'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push("latest")
          }
        }
      }
        }
        }
   }




