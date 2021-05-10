pipeline {
  agent any
  tools {
          maven 'maven381'
          jdk 'JDK904'
        oc 'oc'
    }
            parameters {
                string(name:'CLUSTER_NAME',defaultValue:'openshift-cluster',description:'Cluster name space')
                string(name:'PROJECT_NAME',defaultValue:'etias-sword-dev',description:'Cluster project name')
            }

  stages {

    stage('test'){
       steps {
      echo 'tesing...'
       sh 'mvn test'
       }
        post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
    }
    stage('Build') {
      steps {
        script {
          openshift.withCluster(CLUSTER_NAME) {
           openshift.withProject(PROJECT_NAME) {
            openshift.newApp('--image-stream="openshift/java:11"~https://github.com/filip123go/Simplest-Spring-Boot-Hello-World.git --build-env  MAVEN_OPTS=-Dhttps.protocols=TLSv1.2')
            }
          }
        }
      }
    }
  }
}
