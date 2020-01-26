pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'gradle build'
      }
    }

    stage('Mail Notification') {
      steps {
        mail(subject: 'jenkins', body: 'voila une notification', cc: 'gs_riache@esi.dz')
      }
    }

    stage('Code Analysis') {
      parallel {
        stage('Code Analysis') {
          steps {
            withSonarQubeEnv 'sonar'
            withSonarQubeEnv 'sonar'
          }
        }

        stage('Test Reporting') {
          steps {
            jacoco(buildOverBuild: true, changeBuildStatus: true)
          }
        }

      }
    }

  }
  environment {
    PATH = 'C:\\Windows\\System32'
  }
}