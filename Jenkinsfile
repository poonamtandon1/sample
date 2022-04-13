  pipeline{
    agent any
    environment { 
        registry = "YourDockerhubAccount/YourRepository" 
        registryCredential = 'dockerhub_id' 
        dockerImage = '' 
    }
    tools {
        maven 'maven-3.8.5' 
    }
    
      stages {
               stage ('Compile Stage'){
                   steps {
                      sh "mvn clean install "
                     
                    }
               }
        stage ('Build Docker Image') {
            script { 
17
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 
18
                }
        }
      }
  }
