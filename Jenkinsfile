pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        sh 'echo "Build Stage"'
      }
    }

    stage('Test') {
      steps {
        sh 'echo "Test Stage"'
      }
    }

    stage('Deploy') {
      when {
        branch 'main'
      }
      steps {
        sh '''
        sudo rm -rf jenkinsmultibranch/
        sudo git clone https://github.com/docdoom12345/jenkinsmultibranch.git
        cd jenkinsmultibranch
        sudo yum install httpd -y
        sudo systemctl enable httpd --now
        sudo cp index.html /var/www/html
        '''
      }
    }
  }
