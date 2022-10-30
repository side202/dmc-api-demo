pipeline {
    agent any
    
    stages {

        stage ('Repo') {
            steps {
                checkout scm
            }
        }

        stage ('Build') {
            steps {
               sh "./docker-build.sh ${env.BUILD_NUMBER}"
            }
        }
        
        stage ("Test") {
	    steps {
               sh "echo ejecucion de tests"
            }
	}
	stage ("Upload"){
	    steps {
	      sh "docker push side2022/dmc-api:${env.BUILD_NUMBER}"
	    }
	}

    }
}

