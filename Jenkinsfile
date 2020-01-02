pipeline {
	agent any 
		stages {
			stage('One'){
				steps{
					echo "Hi, this is Marina from Mosaico"
				}
			}
			stage('CI'){
				agent{
					docker{
						reuseNode false
						image 'ubuntu'
						args '--privileged'
						
					}
				}
				steps{
					echo "Running the integration test.."
				}
			}
		} 	
}
