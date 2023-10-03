pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Building pieline'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'Running Unit tests'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'Generating .war file'
        sh 'mvn package -DskipTests'
        archiveArtifacts 'target/*.war'
      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}