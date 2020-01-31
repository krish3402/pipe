pipeline {
  agent any
  stages {
    stage('git') {
      parallel {
        stage('git') {
          steps {
            git 'https://github.com/krish3402/pipe.git'
          }
        }

        stage('backend') {
          steps {
            tool(name: 'maven', type: 'maven')
          }
        }

      }
    }

    stage('Node Install ') {
      steps {
        tool(name: 'nodejs', type: 'nodejs')
        sh 'cd client && npm install'
      }
    }

    stage('Npm Coverage & Test Report') {
      steps {
        sh 'cd client && npm test -- --coverage --watchAll=false'
      }
    }

  }
}