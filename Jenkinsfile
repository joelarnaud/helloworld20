pipeline {
    agent any
    tools {
        maven 'M2_HOME' 
    }
    stages {
      stage('Build'){
        steps {
          echo "Build step"
          sh 'mvn clean'
          sh 'mvn install'
          sh 'mvn package'
        }
      }
        stage('test'){
        steps {
          echo "test step"
          sh 'mvn test'
        }
      }
        stage('deploy'){
        steps {
        echo "deploy step"
        deploy adapters: [tomcat8(credentialsId: 'tomcatID', path: '', url: 'http://35.183.101.53:8000')], contextPath: null, war: '**/*.war'
        }
      }
  }
 }
