pipeline {
  agent any
  stages {
    stage('Build Image') {
      steps {
        script {
          docker.withRegistry('', 'odp-docker'){
            docker.build("test-image:${env.BUILD_ID}")
          }
        }
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
