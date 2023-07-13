pipeline {
  agent any
  stages {
    stage("Remove all Container") {
      steps {
        sh "docker rm -f $(docker ps -aq) || true"
      }
    }
    stage("Building Dockerfile") {
      steps {
        sh "docker build -t jenkinsapp ."
      }
    }
    stage("Prod stage") {
      steps {
        sh "docker run -d -p 80:5500 --name jenkins_container jenkinsapp"
      }
    }
  }
}
