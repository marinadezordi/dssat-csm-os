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
					sh 'rm -rf dssat-csm-os'
					sh 'git clone https://github.com/marinadezordi/dssat-csm-os.git'
					sh 'cp -r Data/* dssat-csm-os/Data'
					sh 'cd dssat-csm-os && git checkout develop && mkdir build'
					sh 'cd dssat-csm-os/build && cmake -DCMAKE_Fortran_COMPILER=/usr/bin/gfortran-8 -DCMAKE_INSTALL_PREFIX=/DSSAT47/A .. && make -j3 && make install'
					sh 'cd dssat-csm-os && git checkout ${env.BRANCH_NAME} && rm -rf build && mkdir build'
				}
			}
		} 	
}
