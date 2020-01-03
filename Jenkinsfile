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
						image 'marinadezordi/imagercroptest:1.0'
					}
				}
				steps{
					sh 'git clone https:github.com/marinadezordi/dssat-csm-os.git'
				}
			}


		} 	
	
}
