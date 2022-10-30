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
	      withCredentials([usernamePassword(credentialsId: "${params.DOCKERHUB_CREDENTIAL}", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                      sh "echo $PASSWORD | docker login -u $USERNAME --password-stdin"
                      sh "docker push mario21ic/dmc-api:${env.BUILD_NUMBER}"
                      sh "docker logout"
	    }
	}
    }
  }
}

