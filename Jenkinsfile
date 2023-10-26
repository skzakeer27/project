pipeline {
  agent any
  tools {
     maven 'Maven-3.9.5' 
  }
  stages{
    stage('Build'){
      steps{
        sh 'mvn clean package'
      }
      post{
        success{
          echo 'archiving the artifact'
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
    stage('Deploy'){
      steps{
        deploy adapters: [tomcat9(credentialsId: '69298ea8-6800-4154-b5e0-0a348d17bad0', path: '', url: 'http://3.110.130.71:8181/')], contextPath: null, war: '**/*.war'
      }
    }
  }
}
