pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh '/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/maven_3.5.2/bin/mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    
	stage ('Deploy to Staging'){
            steps {
                build job: 'Deploy-to-staging'
            }
        }
    }
}
