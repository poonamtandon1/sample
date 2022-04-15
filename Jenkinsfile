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
        when {
            anyOf {
                branch 'develop'; branch 'master'
            }
        }
              steps{
                script {
                  dockerImage = docker.build dockerimagename
                }
              }
            }

        stage('Pushing Image') {
         when { anyOf { branch 'develop'; branch 'master' } }
      environment {
               registryCredential = 'dockerhublogin'
           }
      steps{
       when { anyOf { branch 'develop'; branch 'master' } }
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push("latest")
          }
        }
      }
        }
        stage('Deploying App to Kubernetes') {
         when { anyOf { branch 'develop'; branch 'master' } }
      steps {
        script {
          kubernetesDeploy(configs: "Deployment.yml", kubeconfigId: "kubernetes")

        }
      }
    }
}
  }
