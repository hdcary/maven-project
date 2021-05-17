pipeline {
    agent any
    triggers {
        pollSCM(* * * * *)
    }
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
        stage('Deploy to staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }
        stage('Deploy to production'){
            steps {
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'stage-to-prod'
            }
            post {
                success {
                    echo 'Code deploy to Production.'
                }

                failure {
                    echo 'Deployment failed.'
                }
            }
        }

    }
}