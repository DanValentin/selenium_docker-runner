pipeline{
	agent any
	stages{
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up  --no-color tests-suite"
			}
		}
	}
	post{
		always("Bring everything down"){ 
			archiveArtifacts artifacts: '/d/docker/jenkins/arctest/**'
			bat "docker-compose down"
		}
	}
}