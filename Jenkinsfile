pipeline {
  agent {
    label 'worker1'
  }

  stages {
    stage('Build') {
      steps {
        sh 'echo "Build Stage"'
        sh 'hostname'
      }
    }

    stage('Test') {
      steps {
        sh 'echo "Test Stage"'
        sh 'hostname'
      }
    }

    stage('Deploy') {
      when {
        anyOf {
        branch 'main'
        branch 'tester'
        }
      }
      steps {
        sh '''
        hostname
        sudo yum install httpd -y
        sudo systemctl enable httpd --now
        sudo cp index.html /var/www/html
        '''
      }
    }
  }
}
