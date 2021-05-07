pipeline {
    agent any
        tools {
            maven 'maven381'
        }
        environment {
            MAVEN_OPTS = '-Dhttps.protocols=TLSv1.2'
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