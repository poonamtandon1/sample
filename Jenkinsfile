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
                  withSonarQubeEnv('sonarqube') {
                    sh 'mvn clean verify sonar:sonar'
                  }
                  }
                  }
        stage ('Build Stage'){
          steps{
            sh 'mvn clean install'
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

        }
      }
    }
}
  }
