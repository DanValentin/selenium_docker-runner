//Comanda de pipeline
pipeline{
	//aici specific ca orice agent Jenkins poate executa testele
	agent any
	stages{
		stage("Start Grid"){
			steps{
				//comanda de mai jos porneste Selenium Grid + nodurile Chrome si Firefox in modul "background"
				//folosim "bat" daca rulam pe o masina cu windows, daca rulam pe o masina cu linux folosim "sh"
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				//comanda de mai jos porneste ce suita de teste specificata "test-suite.xml" din fisierul "docker-compose.yaml"
				//folosim "bat" daca rulam pe o masina cu windows, daca rulam pe o masina cu linux folosim "sh"
				bat "docker-compose up  --no-color module-online-order module-search"
			}
		}
	}
	post{
		//comanda "always" este executata mereu indiferent daca build-ul si testele au fost finalizate cu succes sau nu.
		always("Bring everything down"){ 
			//comanda de mai jos opreste toate procesele "Selenium Grid, nodurile Chrome si Firefox + suita de teste.
			//folosim "bat" daca rulam pe o masina cu windows, daca rulam pe o masina cu linux folosim "sh"
			bat "docker-compose down"
		}
	}
}