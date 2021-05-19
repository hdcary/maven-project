pipeline {
    agent any
    tools {
        maven 'localMaven'
    }
    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
                bat "docker build . -t tomcatapp:${env.BUILD_ID}"
            }
        }
    }
}