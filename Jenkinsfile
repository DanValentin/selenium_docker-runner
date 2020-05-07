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
			publishHTML (target: [
				allowMissing: false,
				alwaysLinkToLastBuild: false,
				keepAll: true,
				reportDir: 'D:\docker\outputfiles\docker-compose\module-search',
				reportFiles: 'index.html',
				reportName: "API Unit Testing Results"
			])
		}
	}
}