pipeline {
  agent any
  stages {
    stage('git') {
      parallel {
        stage('git') {
          steps {
            git(url: 'https://github.com/krish3402/pipe.git', branch: 'master')
          }
        }

        stage('backend') {
          steps {
            tool(name: 'maven', type: 'maven')
            sh 'mvn clean install'
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