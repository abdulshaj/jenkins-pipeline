pipeline {
  agent any
  stages {
    stage('Dev') {
      steps {
        sh 'echo "this is Dev server"'
      }
    }

    stage('Test') {
      steps {
        sh 'echo "this is Test server"'
      }
    }

    stage('QA') {
      steps {
        sh 'echo "this is QA server"'
      }
    }

    stage('Release approval') {
      steps {
        input(message: 'Release approval', id: '1', ok: 'Ok')
      }
    }

  }
}