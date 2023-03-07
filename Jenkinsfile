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
        branch 'main && tester'
      }
      steps {
        sh '''
        sudo yum install httpd -y
        sudo systemctl enable httpd --now
        sudo cp index.html /var/www/html
        '''
      }
    }
  }
}
