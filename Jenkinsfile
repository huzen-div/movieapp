// pipeline {
//   environment {
//     imagename = "234563/antsy"
//     registryCredential = 'testt'
//     dockerImage = ''
//   }
//   agent any
//   stages {
//     stage('Cloning Git') {
//       steps {
//         git([url: 'https://github.com/huzen-div/movieapp.git', branch: 'main', credentialsId: 'testt'])

//       }
//     }
//     stage('Building image') {
//       steps{
//         script {
//           dockerImage = docker.build imagename
//         }
//       }
//     }
//     stage('Deploy Image') {
//       steps{
//         script {
//           docker.withRegistry( '', registryCredential ) {
//             dockerImage.push("$BUILD_NUMBER")
//              dockerImage.push('latest')
//           }
//         }
//       }
//     }
//     stage('Remove Unused docker image') {
//       steps{
//         sh "docker rmi $imagename:$BUILD_NUMBER"
//          sh "docker rmi $imagename:latest"

//       }
//     }
//   }
// }

pipeline {
    agent any
    
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }
    }
}