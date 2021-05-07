pipeline {
  agent any
  tools {
        oc 'oc'
    }
  stages {
    stage('Build') {
      steps {
        script {
          openshift.withCluster('etias-sword-dev') {
            openshift.newApp('--image-stream="openshift/java:11" --code=https://github.com/filip123go/Simplest-Spring-Boot-Hello-World.git')
          }
        }
      }
    }
  }
}