pipeline {
  
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('danielbsan-docker-hub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t danielbsan/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push danielbsan/dp-alpine:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
