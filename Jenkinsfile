pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
        sh 'echo "Commit: $(git rev-parse --short HEAD)"'
      }
    }

    stage('Build (demo)') {
      steps {
        sh '''
          mkdir -p dist
          echo "hello from jenkins - $(date)" > dist/build.txt
          echo "[Build] dist/build.txt created"
        '''
      }
    }

    stage('Test (demo)') {
      steps {
        sh '''
          test -f dist/build.txt
          echo "[Test] OK"
        '''
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'dist/**', fingerprint: true
        echo '[Archive] OK'
      }
    }
  }
}
