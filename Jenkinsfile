pipeline {

  environment {
    registry = ""
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/kvetter-materna/bmc2105'
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
