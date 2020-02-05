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

    stage('Npm Test') {
      parallel {
        stage('Npm Test') {
          steps {
            echo 'testing'
          }
        }

        stage('Test') {
          steps {
            sh 'cd client && npm test --watchAll=false'
          }
        }

        stage('Coverage') {
          steps {
            sh 'cd client && npm test -- --coverage --watchAll=false'
          }
        }

      }
    }

    stage('Coverage & Test Report Publish') {
      steps {
        cobertura(enableNewApi: true, sourceEncoding: 'ASCII', coberturaReportFile: 'client/coverage/cobertura-coverage.xml')
        junit 'client/*.xml'
      }
    }

    stage('Maven Install') {
      steps {
        tool(name: 'maven', type: 'maven')
        sh 'mvn --version'
      }
    }

  }
}