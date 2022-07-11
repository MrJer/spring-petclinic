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
          sh './mvnw $SONAR_MAVEN_GOAL'
        }

      }
    }

    stage('Publish') {
      steps {
        sh './mvnw package'
        archiveArtifacts 'target/*.jar'
      }
    }

  }
}