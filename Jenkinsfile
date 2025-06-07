pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/ClockworkYuzu/react-demo.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t react-demo-image .'
      }
    }

    stage('Deploy Container') {
      steps {
        sh '''
          docker rm -f react-demo || true
          docker run -d --name react-demo -p 3000:80 react-demo-image
        '''
      }
    }
  }
}