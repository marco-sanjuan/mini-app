pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        echo 'Checkout from GitHub'
        git(url: 'https://github.com/marco-sanjuan/mini-app', branch: 'master')
      }
    }
    stage('Compile') {
      steps {
        sh 'mvn clean compile'
      }
    }
    stage('Testing') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t mini-app:stable .'
      }
    }

    stage('Deploy to registry') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'password', usernameVariable: 'user')]) {
          sh 'docker tag mini-app:stable marcosanjuan/mini-app:stable'
          sh 'docker push marcosanjuan/mini-app:stable'
        }
      }
    }
  }
}