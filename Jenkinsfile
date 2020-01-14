pipeline {
  agent any
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

        stage('test app') {
          steps {
            sh 'ci/unit-test-app.sh'
          }
        }

      }
    }

  }
}