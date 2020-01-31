pipeline {
  agent any
  stages {
    stage('git') {
      steps {
        git(url: 'https://github.com/krish3402/pipe.git', branch: 'master')
      }
    }

    stage('Node Install ') {
      steps {
        tool(name: 'nodejs', type: 'nodejs')
        sh 'npm config ls && cd client && npm install'
      }
    }

    stage('Npm Coverage & Test Report') {
      steps {
        sh 'cd client && npm test -- --coverage --watchAll=false'
      }
    }

  }
}