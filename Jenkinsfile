pipeline {
  agent any
  stages {
    stage ('Build docker image') {
            steps {
                script {
                    docker.build("test-image:${env.BUILD_ID}")
                }
            }
        }
    }

  }
}
