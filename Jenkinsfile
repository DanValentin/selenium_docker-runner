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
				bat "docker-compose up module-search"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: '/d/docker/outputfiles/**'
			bat "docker-compose down"
		}
	}
}
