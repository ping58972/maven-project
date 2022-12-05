pipeline {
  agent any
//   tools {
//     maven 'localMaven'
//   }
  triggers {
    pollSCM '* * * * *'
  }
  stages {
    stage('checkout') {
      steps {
        // git 'https://github.com/ping58972/practice-jenkinsfile-pipeline.git'
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ping58972/maven-project.git']]])
      }
    }
    stage('Build') {
      steps {
        sh 'whoami'
        sh 'pwd'
        sh 'which java'
        sh 'which mvn'
        sh 'java -version'
        sh 'mvn -version'
        sh 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
