pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/untitled-1.0-SNAPSHOT.jar'
        archiveArtifacts 'build/docs/javadoc/index.html'
        junit 'build/test-results/test/TEST-com.test.MatrixMathematicsTest.xml'
      }
    }

    stage('Email notification') {
      steps {
        mail(subject: 'Email notification', body: 'here is the results of thee first step', cc: 'gs_riache@esi.dz')
      }
    }

    stage('Code analysis') {
      parallel {
        stage('Code analysis') {
          steps {
            withSonarQubeEnv('sonar') {
              bat 'gradle sonarqube'
            }

            waitForQualityGate true
          }
        }

        stage('Test Reporting') {
          steps {
            jacoco(execPattern: 'build/jacoco/*.exec\'', sourcePattern: 'src/main/java', inclusionPattern: '**/*.class', classPattern: 'build/classes')
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        bat 'gradle publish'
      }
    }

    stage('Slack Notification') {
      steps {
        slackSend(baseUrl: 'https://hooks.slack.com/services/', channel: 'gd_dada', token: 'TT638QSA3/BTGR6T21L/Me5FiArLCJaE9t7QhUjbkq8R')
      }
    }

  }
}