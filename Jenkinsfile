pipeline {
  agent any
  stages {
    stage('Parallel execution') {
      parallel {
        stage('Say hello') {
          steps {
            sh 'echo "Hello my dear World"'
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

      }
    }

  }
}