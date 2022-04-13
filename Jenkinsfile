  pipeline{
    agent any
    environment { 
3
        registry = "YourDockerhubAccount/YourRepository" 
4
        registryCredential = 'dockerhub_id' 
5
        dockerImage = '' 
6
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
