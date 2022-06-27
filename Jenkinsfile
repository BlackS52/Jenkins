// Declarative method 
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
	stage('Clone OpenMPI') { 
		steps {			
			echo '*** Clone ***************'
//			sh 'git clone ${GIT_OMPIFORK}'
			sh 'git fetch ${GIT_OMPIFORK}'
			sh 'pwd'
		} 
	} // Clone OpenMPI

	stage('Clone PMIx') { 
		steps {			
			echo '*** Clone PMIx ***************'
			sh 'cd ompi_fork/3rd-party/ && git clone ${GIT_PMIX} && pwd'
		}
	} // Clone PMIx

	stage('Clone PRRTE') { 
		steps {			
			echo '*** Clone PRRTE **************'
			sh 'cd ompi_fork/3rd-party/ && git clone ${GIT_PRRTE} && pwd'
		}
	} // Clone PRRTE

/*	stage('Build OpenMPI ') { 
		steps {			
			echo '*** Build OpenMPI ***************'
			sh 'pwd'
			sh 'cd ompi_fork/ && ./autogen.pl'

//			sh 'cp -Rp openpmix ompi_fork/3rd-party/'
			// yum install gcc flex libevent-devel.x86_64 hwloc-devel -y
			// Should be close to this /home/mpi_test/pmix/openpmix_build
//			sh 'cd openpmix/ && ./autogen.pl && ./configure --prefix=$PWD/../openpmix_build && make && make install'
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
