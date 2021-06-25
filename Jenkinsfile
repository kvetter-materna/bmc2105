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

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "nginx-deployment.yaml", kubeconfigId: "kube_access")
        }
      }
    }

  }

}
