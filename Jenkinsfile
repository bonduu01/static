pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
          sh 'echo "Hello World"'
          sh '''
             echo "Multiline lines shells works too"
             ls -ali
             '''
        }
      }
    }
  }
