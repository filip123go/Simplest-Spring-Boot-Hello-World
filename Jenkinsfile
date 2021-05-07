pipeline {
    agent any
        environment {
         echo 'Setting up environment variables'
            MAVEN_OPTS = '-Dhttps.protocols=TLSv1.2'
        }
    stages {
        stage("build") {
            steps {
                echo 'building the application...'
            }
        }
        stage("test") {
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