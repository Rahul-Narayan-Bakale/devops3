pipeline {
   agent any

  environment {
    DOCKERHUB_CREDENTIALS = 'ClogMachine'
    IMAGE_NAME = 'rahulnb379/dockerimg'
  }

  stages {
    stage('Build Java Application') {
      steps {
        bat 'javac helloWorld.java'
      }
    }

    stage('Build Docker Image') {
      step {
        bat 'docker build -t %IMAGE_NAME%:latest .'
      }
    }

    stage('Login to Dockerhub') {
      steps{
        withCredentials([usernamePassword(
          credentialsId: 'ClogMachine',
          usernameVariable: 'rahulnb379', 
           passwordVariable: 'Rahulnb74')]) {

              bat 'echo %PASS%| docker login -u %USER% --password-stdin'
        }
      }
    }

     stage('Push Docker Image') {
        steps {
           bat 'docker push %IMAGE_NAME%:latest'
        }
     }
  }
}
