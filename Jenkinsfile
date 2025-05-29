pipeline {
  agent any

  tools {
    nodejs 'NodeJS_18' // Make sure this matches the tool name configured in Jenkins
  }

  environment {
    FRONTEND_DIR = 'frontend'   // update this path if your React app is in a different folder
    BACKEND_DIR = 'backend'     // update this path if your Node backend is in a different folder
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/mdevigit/devops.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        script {
          echo 'Installing dependencies for frontend and backend...'
          dir("${FRONTEND_DIR}") {
            sh 'npm install'
          }
          dir("${BACKEND_DIR}") {
            sh 'npm install'
          }
        }
      }
    }

    stage('Lint') {
      steps {
        script {
          echo 'Running linters...'
          dir("${FRONTEND_DIR}") {
            sh 'npx eslint .'
          }
          dir("${BACKEND_DIR}") {
            sh 'npx eslint .'
          }
        }
      }
    }

    stage('Test') {
      steps {
        script {
          echo 'Running tests...'
          dir("${FRONTEND_DIR}") {
            sh 'npm test'  // assuming using Jest/React Testing Library
          }
          dir("${BACKEND_DIR}") {
            sh 'npm test'  // assuming using Mocha/Jest
          }
        }
      }
    }

    stage('Build') {
      steps {
        script {
          echo 'Building frontend...'
          dir("${FRONTEND_DIR}") {
            sh 'npm run build'
          }
          echo 'Preparing backend...'
          dir("${BACKEND_DIR}") {
            // Optional: transpile, bundle, etc.
            echo 'No build step for backend, skipping...'
          }
        }
      }
    }
  }
}
