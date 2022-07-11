pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh './mvnw compile'
      }
    }

    stage('SonarQube') {
      steps {
        withSonarQubeEnv 'SonarQube'
        waitForQualityGate(credentialsId: 'SonarQube', abortPipeline: true)
      }
    }

    stage('Publish') {
      steps {
        sh './mvnw package'
      }
    }

  }
}