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
						reuseNode false
						image 'marinadezordi:1.0'
					}
				}
				steps{
					echo 'Running the integration test..'
				}
			}


		} 	
	
}
