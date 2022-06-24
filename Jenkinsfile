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


	environment {
   	SSISBuildPath="/home/mpi_test/jenkins_stuff/ompi/"
		SSISDeployPath="/home/mpi_test/jenkins_stuff/ompi_install"
	}

#	docker { image 'python:3.10.1-alpine' } 
#	}
*/
   stages {
	stage('check') { 
        	steps {
			echo '*** Check ***************'
               		sh 'python --version'
        	}
	stage('Clone base project') { 
		steps {
			echo '*** Clone ***************'
			sh "git clone https://github.com/BlackS52/ompi_fork.git"
		}
	}
// 		stage('Deploy') { }       
   	}
    }
}
