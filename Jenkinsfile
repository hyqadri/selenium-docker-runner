pipeline {
    agent any
    stages {
		stage('pull latest image') {
            steps {
                sh "docker pull hyousaf/selenium-docker"
            }            
        }
        stage('start grid') {
            steps {
                sh "docker-compose up -d chrome firefox"
            }            
        }
        stage('run test') {
            steps {
               sh "docker-compose up TS_Acceptance
            }
        }       
    }
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
		}
	}
}