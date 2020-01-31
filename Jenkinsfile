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
        sh 'cd client && npm install'
      }
    }

    stage('Npm Coverage & Test Report') {
      steps {
        sh 'cd client && npm test -- --coverage --watchAll=false'
      }
    }

stage('git') {
      parallel {
stage('maven install') {
          steps {
            tool(name: 'maven', type: 'maven')
            sh 'mvn clean install'
          }
        }

      }
    }
  }
