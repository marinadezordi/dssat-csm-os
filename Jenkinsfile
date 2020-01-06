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
					sh 'cd /home/cidssat/'
					sh 'git clone https://github.com/marinadezordi/dssat-csm-os.git'
					sh 'cp -r Data/* dssat-csm-os/Data'
					sh 'cd dssat-csm-os && git checkout develop && mkdir build'
					sh 'cd build && cmake -DCMAKE_Fortran_COMPILER=/usr/bin/gfortran-8 -DCMAKE_INSTALL_PREFIX=/DSSAT47/A .. && make -j3 && make install'
					sh 'cd /home/cidssat/dssat-csm-os && git checkout ${BRANCH_NAME} && rm -rf build && mkdir build'
					sh 'cd build && cmake -DCMAKE_Fortran_COMPILER=/usr/bin/gfortran-8 -DCMAKE_INSTALL_PREFIX=/DSSAT47/B .. && make -j3 && make install'
					sh 'cd /DSSAT47/A/ci && ../run_dssat B AllCrops.v47'
					sh 'ls /DSSAT47/A'
					sh 'cd /DSSAT47/B/ci && ../run_dssat B AllCrops.v47'
					sh 'cd /home/test && Rscript citest.R'
				}
			}
		} 	
}
