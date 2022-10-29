pipeline {
  agent any

  stages {

    stage ("Repo") {
      steps {
        checkout scm
      }
    }

    stage ("Build") {
      steps {
        sh "./docker-build.sh ${env.BUILD_NUMBER}"
      }
    }

    stage ("Test") {
      steps {
        sh "echo 'ejecucion de tests'"
      }
    }

    stage ("Upload") {
      steps {
        // TODO mejorar con script
        sh "docker push mario21ic/dmc-api:${env.BUILD_NUMBER}"
      }
    }

  }
}
