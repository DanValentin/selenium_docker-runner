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
				publishHTML (target: [
				allowMissing: false,
				alwaysLinkToLastBuild: false,
				keepAll: true,
				reportDir: '/usr/share/proiectlicenta/test-output',
				reportFiles: 'index.html',
				reportName: "API Unit Testing Results"
			])
			}
		}
	}
	post{
		always{ 
			bat "docker-compose down"
		}
	}
}