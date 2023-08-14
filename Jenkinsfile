pipeline {
  agent any 
  environment {
    PATH = "$PATH:/opt/maven/bin"
  }
  stages {
    stage('getcode') {
      steps {
        git 'https://github.com/koneti0021/SonarQube-pipeline.git'
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean install package'
      }
    }
    stage('SonarQube analysis') {
      steps {
        withSonarQubeEnv('SonarQube-9.9') {
          sh "mvn sonar:sonar"
        }
      }
    }
  }
}
          
