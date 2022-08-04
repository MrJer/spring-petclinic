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
        sh 'cp target/*.jar /var/ansible/files/target'
        ansiblePlaybook(playbook: '/var/ansible/playbook.yaml', inventory: '/etc/ansible/hosts')
      }
    }

  }
}