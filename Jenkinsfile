pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        script {
          sh 'kubectl apply -f k8s-manifests/deployment.yaml'
          sh 'kubectl apply -f k8s-manifests/service.yaml'
        }
      }
    }
    stage('Test Application') {
      steps {
        script {
          sh 'kubectl get pods'
          sh 'curl -f http://localhost:85'
        }
      }
    }
  }
}
