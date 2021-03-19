pipeline {
  agent any
  stages {
    stage('Build Image') {
      steps {
        script {
          docker.build("test-image:${env.BUILD_ID}")
        }

      }
    }

    stage('Anchore Scan') {
      steps {
        anchore(name: 'Dockerfile', engineCredentialsId: 'anchore-jenkins-test', engineRetries: '3', engineurl: 'https://anchore.gsa.gov:8228/v1', policyBundleId: '25d3270c-7fc5-444e-8eb2-e421b49f551a')
      }
    }

  }
}