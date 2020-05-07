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
			allure includeProperties: false, jdk: '', results: [[path: 'D:\\docker\\jenkins\\slaves\\Slave_1\\workspace\\allure-results']]
		}
	}
}