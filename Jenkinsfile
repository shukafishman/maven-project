pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    tools {
        maven 'local_maven'
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging') {
            steps {
                build job: 'deploy-to-staging'
            }
        }
    }

}
