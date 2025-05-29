pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/mdevigit/devops.git'
      }
    }

    stage('Lint Frontend') {
      steps {
        dir('frontend') {
          sh 'npm install'
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

    stage('Lint Backend') {
      steps {
        dir('backend') {
          sh 'npm install'
          sh 'npm run lint'
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

    stage('Build Docker Images') {
      steps {
        sh 'docker-compose build'
      }
    }

    stage('Deploy App') {
      steps {
        sh 'docker-compose up -d'
      }
