pipeline {
  environment {
    imagename = "234563/antsy"
    DOCKER_HOME = '/usr/local/bin/docker'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/huzen-div/movieapp.git', branch: 'main', credentialsId: 'testt'])
      }
    }
    stage('Build image'){
      steps{
        script{
          sh '${DOCKER_HOME} build -t ${imagename}:latest .'
        }
      }
    }
    stage('Push image to Hub'){
      steps{
        script{
          withCredentials([usernamePassword(credentialsId: '3a3d2229-4a91-4d17-91bf-130069bef1ea	', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
            sh '${DOCKER_HOME} login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}'
            //sh '${DOCKER_HOME} tag discovery-service:latest janescience/discovery-service:latest'
            sh '${DOCKER_HOME} push ${imagename}:latest'
            sh '${DOCKER_HOME} rmi -f $(${DOCKER_HOME} images -f "dangling=true" -q)'
          }
        }
      }
    }
    stage('Deployment'){
      steps{
        script{
          sh '/usr/local/bin/kubectl apply -f pod.yaml'
          sh '/usr/local/bin/kubectl apply -f service.yaml'
        }
      }
    }
  }
}