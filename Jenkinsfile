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
				bat "docker-compose up  --no-color module-search module-book-flight"
			}
		}
	}
	post{
		always{ 
			bat "docker-compose down"
		}
	}
}