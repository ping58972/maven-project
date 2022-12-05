pipeline {
  agent any
//   tools {
//     maven 'M3'
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
