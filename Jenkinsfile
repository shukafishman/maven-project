pipeline {
    agent any

    tools {
        maven 'local_maven'
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package'
                sh 'docker build . -t tomcat:${env.BUILD_ID}'
            }
        }
    }
}
