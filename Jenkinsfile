pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/untitled-1.0-SNAPSHOT.jar'
        archiveArtifacts 'build/docs/javadoc'
      }
    }

  }
}