pipeline {
	agent any
	environment {
		PATH = "/usr/local/bin:$PATH"
		}
		stages {
			stage('One'){
				steps{
					echo "Hi, this is Marina from Mosaico"
				}
			}
			stage('CI'){
				agent{
					docker{
						args '--privileged'
						image 'ubuntu'
					}
				}
				steps{
					echo "Running the integration test.."
				}
			}
		} 	
}
