pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/mdevigit/devops.git'
      }
    }
    stage('Install Frontend') {
      steps {
        dir('frontend') {
          sh 'npm install'
        }
      }
    }
    stage('Install Backend') {
      steps {
        dir('backend') {
          sh 'npm install'
        }
      }
    }
    stage('Lint Frontend') {
      steps {
        dir('frontend') {
          sh 'npm run lint'
        }
      }
    }
    stage('Lint Backend') {
      steps {
        dir('backend') {
          sh 'npm run lint'
        }
      }
    }
    stage('Test Frontend') {
      steps {
        dir('frontend') {
          sh 'npm test'
        }
      }
    }
    stage('Test Backend') {
      steps {
        dir('backend') {
          sh 'npm test'
        }
      }
    }
  }
}
