pipeline {
  environment {
    imagename = "234563/antsy"
    registryCredential = 'testt'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/huzen-div/movieapp.git', branch: 'main', credentialsId: 'testt'])

      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build imagename
        }
      }
    }
    
  }
}
