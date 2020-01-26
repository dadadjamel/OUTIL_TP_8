pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        build(job: 'gradle', propagate: true, wait: true)
      }
    }

  }
}