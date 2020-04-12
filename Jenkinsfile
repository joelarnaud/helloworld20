pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
   
    stage ('build') {
        steps {
          echo "deploy step"
            deploy (adapters: [tomcat8(credentialsId: 'tomcatID', path: '', url: 'https://99.79.65.66:8080')], contextPath: null, war: '**/.*war')
        }
      }
    }
}
