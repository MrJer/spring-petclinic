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
        withSonarQubeEnv('SonarQube') {
          sh './mvnw compile'
        }

      }
    }

    stage('Publish') {
      steps {
        sh './mvnw package'
      }
    }

  }
}