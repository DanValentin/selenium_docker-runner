pipeline{
	agent any
	stages{
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d --no-color hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up --no-color module-search"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'docker-compose/**'
			bat "docker-compose down"
		}
	}
}
