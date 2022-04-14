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
        stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "Deployment.yml", kubeconfigId: "kubernetes")
          kubernetesDeploy(configs: "Service.yml", kubeconfigId: "kubernetes")
        }
      }
    }
}
  }
