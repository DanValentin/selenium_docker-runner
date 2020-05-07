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
				bat "docker-compose up  --no-color module-search"
			}
		}
	}
	post{
		always{ 
			bat "docker-compose down"
			step([$class: 'Publisher', reportFilenamePattern: '**/testng-results.xml'])
		}
	}
}