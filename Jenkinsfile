pipeline {
  agent any
  stages {
    stage('Dev') {
      steps {
        sh 'echo "this is Dev server"'
        sh '''ssh -o StrictHostKeyChecking=no ubuntu@${13.234.119.105}
                        # Kill Java process
                        sudo fuser -k 80/tcp
                        # Clone the repository if not already done
                        if [ ! -d .git ]; then
                            git clone https://github.com/TestLeafInc/jenkins-pipeline
                        fi
                        # Pull latest code
                        cd /home/ubuntu/jenkins-pipeline/leafhub
                        git pull
                        # Store commit ID
                        export COMMIT_ID=$(git rev-parse HEAD)
                        # Run maven spring boot
                        nohup sudo mvn spring-boot:run > /dev/null 2>&1 &'''
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