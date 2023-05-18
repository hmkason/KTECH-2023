pipeline {
  agent any
  tools {
     maven 'M2_HOME'
  }
  environment {
     registry = "atabonglefac/DockerHub_Credentials"
     registryCredential = 'DockerHub_Credentials'
  }
  stages {
    stage('Build'){
      steps {
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
      script {
       docker.build registry + ":$BUILD_NUMBER"
      }
     }
   }
  }
}
