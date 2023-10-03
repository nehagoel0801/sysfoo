pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Building pieline'
        sh 'mvn compile'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit tests') {
          steps {
            echo 'Running Unit tests'
            sh 'mvn clean test'
          }
        }

        stage('Integration tests') {
          steps {
            sleep 5
          }
        }

        stage('SCA') {
          steps {
            sleep 8
          }
        }

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