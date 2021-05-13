pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh '/home/vagrant/apache-maven-3.8.1/bin/mvn clean package'
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