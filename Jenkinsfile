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
  }
}