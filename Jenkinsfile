pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'D:\\\\gradle-5.4.1\\\\bin\\\\gradle build'
      }
    }

    stage('Mail Notification') {
      steps {
        mail(subject: 'jenkins', body: 'voila une notification', cc: 'gs_riache@esi.dz')
        mail(subject: 'mail notif', body: 'mail notif', cc: 'gs_riache@esi.dz ')
      }
    }

    stage('Test Reporting') {
      steps {
        jacoco(buildOverBuild: true, changeBuildStatus: true)
        withSonarQubeEnv 'sonar'
      }
    }

  }
  environment {
    PATH = 'C:\\Windows\\System32'
  }
}