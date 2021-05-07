pipeline {
  agent any
  tools {
        oc 'oc'
    }
            parameters {
                string(name:'MAVEN_OPTS',defaultValue:'-Dhttps.protocols=TLSv1.2',description:'setup the correct tls protocol for openshift')
                string(name:'CLUSTER_NAME',defaultValue:'openshift-cluster',description:'Cluster name space')
                string(name:'PROJECT_NAME',defaultValue:'etias-sword-dev',description:'project name space')
            }

  stages {
    stage('Build') {
      steps {
        script {
          openshift.withCluster(CLUSTER_NAME) {
            openshift.newApp('--image-stream="openshift/java:11" --code=https://github.com/filip123go/Simplest-Spring-Boot-Hello-World.git')
          }
        }
      }
    }
  }
}