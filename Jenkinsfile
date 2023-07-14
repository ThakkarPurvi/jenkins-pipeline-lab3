pipeline {
  agent any
  stages {
    stage("Remove all container") {
      steps {
        sh "docker rm -f \$(docker ps -aq) || true"
      }
    }
    stage("Build docker image") {
      steps {
        sh "docker build -t jenkinsapp ."
      }
    }
    stage("Run the container") {
      steps {
        sh "docker run -d -p 80:5500 --name jenkins_container jenkinsapp"
      }
    }
  }
}
