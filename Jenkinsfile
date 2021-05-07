pipeline {
    agent any
        environment {
            MAVEN_OPTS = '-Dhttps.protocols=TLSv1.2'
        }
    stages {
        stage("build") {
            steps {
                echo 'building the application...'
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