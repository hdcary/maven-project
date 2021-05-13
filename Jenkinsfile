pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh '/var/lib/jenkins/apache-maven-3.8.1/bin/mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}