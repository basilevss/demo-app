pipeline {
  agent any

  options {
    timestamps()
  }

  stages {
    stage('Checkout') {
          steps {
            checkout scm
          }
          }

    stage('Setup'){
      steps {
        sh 'python3 -m venv venv'
        sh './venv/bin/pip install --upgrade pip'
        sh './venv/bin/pip install -r requirements.txt'
      }
    }

    stage('Build'){
      steps {
        sh './venv/bin/pytest --junitxml=result.xml'
      }
    }
          }
    stage('Test'){
      steps {
        sh './venv/bin/pytest --junitxml=result.xml'
      }
    }
          }

post {
  always {
    junit 'result.xml'
  }

  success {
    echo 'Sborka uspeshna'
  }

  failure {
    echo 'Sborka error'
  }
}
          }
