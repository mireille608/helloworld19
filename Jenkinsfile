pipeline {
  agent any
  tools{
    mavern 'M2_HOME'
  }
  environment {
    registry = "mireille2012/devop-pipeline"
    registryCredential = 'dockerID'
}
  stages{
    stage('build'){
      steps{
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
      }
    }
     stage('test'){
      steps{
        echo "test step"
        sh 'mvn test'
      }
    }
     stage('deploy'){
      steps{
       script {
        docker.build registry + ":$BUILD_NUMBER"
       }
      }
     } 
  }
}
