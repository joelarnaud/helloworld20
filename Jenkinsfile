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
        sshPublisher(publishers: [sshPublisherDesc(configName: 'Docker-host', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'docker rmi -f image:v.${BUILD_NUMBER}; docker buidl -t image:v.${BUILD_NUMBER} .; docker tag image:v.${BUILD_NUMBER} joelarnaud/image:v.${BUILD_NUMBER}; docker push joelarnaud/image:v.${BUILD_NUMBER}', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        }
      }
  }
 }
