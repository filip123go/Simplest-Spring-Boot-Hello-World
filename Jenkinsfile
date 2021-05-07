pipeline {
  agent any
  tools {
          maven 'maven381'
          jdk 'JDK904'
        oc 'oc'
    }
            parameters {
                string(name:'CLUSTER_NAME',defaultValue:'openshift-cluster',description:'Cluster name space')
                string(name:'PROJECT_NAME',defaultValue:'simplest-spring-boot-hello-world',description:'Cluster project name')
            }

  stages {
    stage('Build') {
      steps {
        script {
          openshift.withCluster(CLUSTER_NAME) {
           openshift.withProject(PROJECT_NAME) {
            openshift.login('--token=8p7xwWeI5HSWg8-cXctSlaeABKiOiMv0q2vKopB8K-w --server=https://api.okd-cluster.okd.local:6443')
            openshift.newApp('openshift/java:11~https://github.com/filip123go/Simplest-Spring-Boot-Hello-World.git')
            }
          }
        }
      }
    }
  }
}