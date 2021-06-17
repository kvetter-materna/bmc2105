pipeline {

  environment {
    registry = "314068309843.dkr.ecr.eu-central-1.amazonaws.com"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/kvetter-materna/bmc2105.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
          docker.withRegistry( "" ) {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "nginx-deployment.yaml", kubeconfigId: "kube_access")
        }
      }
    }

  }

}
