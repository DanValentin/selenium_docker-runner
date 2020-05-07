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
				publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/d/docker/outputfiles/docker-compose/module-search', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
				)
			}
		}
	}
	post{
		always{ 
			bat "docker-compose down"
		}
	}
}