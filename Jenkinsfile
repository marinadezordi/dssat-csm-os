pipeline {
	agent any 
		stages {
			stage('One'){
                steps{
				echo 'Hi, this is Marina from Mosaico'	
                }
			}
			stage('CI'){
				agent{
					 docker{
						withTool('docker'){
						image 'ubuntu'
						 }
						 reuseNode false

					}
				}
				steps{
					echo 'Running the integration test..'
				}
			}


		} 	
	
}
