  pipeline{
     agent any
      stages {
               stage ('Compile Stage'){
                   steps {
                    withMaven(maven: 'M3', mavenSettingsConfig: 'mvn-setting-xml') {
                         sh "mvn clean install "
                     }
                    }
               }
      }
  }
