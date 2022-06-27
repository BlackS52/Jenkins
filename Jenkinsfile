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
	}

   stages {
	stage('check') { 
        	steps {
			echo '*** Check ***************'
               		sh 'python --version'
        	}

   	} // check
	stage('Clone base project') { 
		steps {			
			echo '*** Clone ***************'
			sh 'git clone ${GIT_OMPIFORK}'

			sh 'pwd'
		}
	
	} // Clone
	post {
		success {
			echo "***** Clone successfully done ***"
		}
		failure {
			echo "***** Clone is done with failure ***"
		}
	}
    }
}
