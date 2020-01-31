pipeline {
  agent any
  stages {
    stage('git') {
      steps {
        git 'https://github.com/krish3402/pipe.git'
      }
    }

    stage('Node Install ') {
      steps {
        tool(name: 'nodejs', type: 'nodejs')
        sh 'cd client && npm install'
      }
    }

  }
}