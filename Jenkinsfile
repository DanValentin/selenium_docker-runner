pipeline{
	agent any
	stages{
		stage("Start Grid"){
			steps{
				sh "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up module-search"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: '/d/docker/outputfiles/**'
			sh "docker-compose down"
		}
	}
}