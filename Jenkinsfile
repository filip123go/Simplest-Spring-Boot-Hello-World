pipeline {
  agent any
  stages {
    stage('Build') {
      when {
        expression {
          openshift.withCluster() {
            return !openshift.selector('bc', 'mapit-spring').exists();
          }
        }
      }
      steps {
        script {
          openshift.withCluster() {
            openshift.newApp('--image-stream="openshift/java:11" --code=https://github.com/filip123go/Simplest-Spring-Boot-Hello-World.git')
          }
        }
      }
    }
  }
}