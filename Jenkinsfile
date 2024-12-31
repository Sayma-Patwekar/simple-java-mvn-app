pipeline {
  agent any
  stages {
    stage('mvn version') {
      steps {
        sh 'echo Print mvn version'
        sh 'mvn -v'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
        archiveArtifacts 'target/my-app-*.jar'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }

  }
  tools {
    maven 'mvn399'
  }
}