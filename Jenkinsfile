pipeline {
    agent any
    tools {
        maven 'Maven 3.8.6'
    }
    stages {
        stage ('Initialize') {
            sh '''
                echo "PATH = ${PATH}"
            '''
        }
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
    }
}
