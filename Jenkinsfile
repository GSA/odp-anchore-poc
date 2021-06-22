pipeline {
  agent any
  stages {
    stage('Build Image') {
      steps {
        script {
          docker.build("test-image:${env.BUILD_ID}")
        }

        sh '''whoami

docker ps -a'''
      }
    }

    stage('Anchore Scan') {
      steps {
        writeFile(text: 'debian:latest', file: 'anchore_images')
        anchore(name: 'anchore_images', engineCredentialsId: 'anchore-jenkins-test', engineurl: 'https://anchore.gsa.gov/v1')
      }
    }

  }
}