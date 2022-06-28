// Declarative method 

// *******************************************
// Target: gather all needs in one place 
//	and build OpenMPI
//*******************************************

pipeline {
	agent any
/*	agent { 
		node { label 'first_pancake' }
	}
*/
/*
	parameters {
    	booleanParam(defaultValue: true, description: 'Build OMPI', name: 'BUILD')
    	booleanParam(defaultValue: true, description: 'Deploy OMPI', name: 'DEPLOY')
    	booleanParam(defaultValue: false, description: 'Remove OMPI', name: 'REMOVE')
	}
*/

	environment {
   		GIT_OMPIFORK="https://github.com/BlackS52/ompi_fork.git"
		GIT_PMIX="https://github.com/openpmix/openpmix.git"
		GIT_PRRTE="https://github.com/openpmix/prrte.git"
	}

   stages {
	stage('check') { 
        	steps {
			echo '*** Check ***************'
               		sh 'python --version'
        	}

   	} // check
	
	stage('Build') {
		stages { 
			stage('Clone OpenMPI') { 
				steps {			
					echo '*** Clone ***************'
					sh 'git fetch ${GIT_OMPIFORK}'
					sh 'pwd'
				} 
			} // Clone OpenMPI

			stage('Clone PMIx') { 
				steps {			
					echo '*** Clone PMIx ***************'
					sh 'cd ompi_fork/3rd-party/ && git fetch ${GIT_PMIX} && pwd'
				}
			} // Clone PMIx

			stage('Clone PRRTE') { 
				steps {			
					echo '*** Clone PRRTE **************'
					sh 'cd ompi_fork/3rd-party/ && git fetch ${GIT_PRRTE} && pwd'
				}
			} // Clone PRRTE

			stage('Build OpenMPI ') { 
				steps {			
					echo '*** Build OpenMPI ***************'
					sh 'pwd'
					// yum install gcc flex libevent-devel.x86_64 hwloc-devel -y
					sh 'cd ompi_fork/ && ./autogen.pl && ./configure --prefix=$PWD/../openmpi_build && make && make install && pwd'
				}	
			} // Build OpenMPI
		}
	} // Build 
/*	stage('Clone OpenMPI') { 
		steps {			
			echo '*** Clone ***************'
			sh 'git fetch ${GIT_OMPIFORK}'
			sh 'pwd'
		} 
	} // Clone OpenMPI

	stage('Clone PMIx') { 
		steps {			
			echo '*** Clone PMIx ***************'
			sh 'cd ompi_fork/3rd-party/ && git fetch ${GIT_PMIX} && pwd'
		}
	} // Clone PMIx

	stage('Clone PRRTE') { 
		steps {			
			echo '*** Clone PRRTE **************'
			sh 'cd ompi_fork/3rd-party/ && git fetch ${GIT_PRRTE} && pwd'
		}
	} // Clone PRRTE

	stage('Build OpenMPI ') { 
		steps {			
			echo '*** Build OpenMPI ***************'
			sh 'pwd'
			// yum install gcc flex libevent-devel.x86_64 hwloc-devel -y
			sh 'cd ompi_fork/ && ./autogen.pl && ./configure --prefix=$PWD/../openmpi_build && make && make install && pwd'
		}	
	} // Build
*/

   } // stages
   post {
	success {
		echo '***** Clone successfully done ***'
	}
	failure {
		echo '***** Clone is done with failure ***'
	}
   } // post
} // pipeline
