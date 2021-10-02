pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        node {
          label 'build-agent'
        }

      }
      steps {
        sh '''npm ci
npm run'''
      }
    }

    stage('Test') {
      steps {
        sh '''npm install cypress
npm install mocha npx cypress run --spec ./cypress/integration/test.spec.js'''
      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            sh 'echo "Hello World"'
          }
        }

        stage('post') {
          steps {
            junit 'results/cypress-report.xml'
          }
        }

      }
    }

  }
}