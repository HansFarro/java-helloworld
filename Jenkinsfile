pipeline {
  agent any

  tools {
    maven 'Maven3'
    jdk 'JDK8'
  }

  stages {
    stage('Build') {
      steps {
        script {
          if (isUnix()) {
            sh 'mvn --batch-mode compile'
          }
          else {
            bat 'mvn --batch-mode compile'
          }
        }
      }
    }

    stage('Package') {
      steps {
        script {
          if (isUnix()) {
            sh 'mvn --batch-mode jar:jar'
          }
          else {
            bat 'mvn --batch-mode jar:jar'
          }
        }
      }
    }

    stage('Install'){
      steps {
        script {
          if (isUnix()) {
            sh 'mvn --batch-mode jar:jar source:jar install:install'
          }
          else {
            bat 'mvn --batch-mode jar:jar source:jar install:install'
          }
        }
      }
    }
  }
}