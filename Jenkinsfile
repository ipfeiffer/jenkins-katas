pipeline {
  agent {
    node {
      label 'host'
    }

  }
  stages {
    stage('Parallel execution') {
      parallel {
        stage('Say hello') {
          steps {
            sh 'echo "Hello my dear World"'
            sh 'echo "Hello to all others"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh '''ci/build-app.sh
'''
          }
        }

        stage('clone down') {
          agent {
            node {
              label 'host'
            }

          }
          steps {
            stash(name: 'code', excludes: '.git')
          }
        }

      }
    }

  }
}