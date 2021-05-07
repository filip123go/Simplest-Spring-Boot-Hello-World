pipeline {
    agent any
        tools {
            maven 'maven381'
        }
        environment {
            MAVEN_OPTS = '-Dhttps.protocols=TLSv1.2'
        }
        parameters {
            string(name:'MAVEN_OPTS',defaultValue:'-Dhttps.protocols=TLSv1.2',description:'setup the correct tls protocol for openshift')
        }
    stages {
        stage("build") {
            steps {
                echo 'building the application...'
                echo "building with env variables ${MAVEN_OPTS}..."
                sh "mvn install"
            }
        }
        stage("test") {
            when {
                expression {
                    env.BRANCH_NAME == 'dev'
                }
            }
            steps {
                 echo 'testing the application...'
            }
        }
        stage("deploy") {
            steps {
                 echo 'building the deploying...'
            }
        }
    }
}