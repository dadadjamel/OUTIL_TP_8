pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        slackSend(baseUrl: 'https://hooks.slack.com/services/', token: 'TT638QSA3/BT4BW8HGQ/oASx9sxgMpLc9xZF9tAVSCe5', teamDomain: 'outiltp8', channel: 'gd_dada', message: 'test_tp8')
      }
    }

  }
  environment {
    PATH = 'C:\\Windows\\System32'
  }
}