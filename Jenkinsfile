pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                sh 'npm install --prefix frontend'
                sh 'npm install --prefix backend'
            }
        }

        stage('Test') {
            steps {
