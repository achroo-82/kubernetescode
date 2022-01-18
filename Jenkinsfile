pipeline {

    agent any

    environment {
        registry = "achroo/kubernetescode"
        registryCredential = 'dockerhub'
     }

    stages{


        stage('Building image') {
           steps{
              script {
                      dockerImage = docker.build registry + ":$BUILD_NUMBER"
                  }
              }
        }

        stage('Deploy Image') {
           steps{
              script {
                 docker.withRegistry( '', registryCredential ) {
                 dockerImage.push("$BUILD_NUMBER")
                 dockerImage.push('latest')
                 }
              }
           }
        }
    }

}