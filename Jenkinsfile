  pipeline{
 
tools{
       maven 'Apache Maven 3.3'
       // without mavenSettingsConfig, my settings.xml is not used.  With it, this blows up
       mavenSettingsConfig: 'Global Maven Settings'
       jdk 'jdk9
   }
      stages {
               stage ('Compile Stage'){
                    steps {
                    sh 'mvn clean compile'
                  }
               }
      }
  }
