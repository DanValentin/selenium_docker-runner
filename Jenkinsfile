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
				bat "docker-compose up  --no-color module-online-order module-book-flight module-search.xml"
			}
		}
	}
	post{
		always{ 
			bat "docker-compose down"
		}
	}
}