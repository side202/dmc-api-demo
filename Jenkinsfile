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
        parallel (
          unit: {
            echo "pruebas unitarias"
          },
          syntax: {
            echo "pruebas de sintaxis"
          },
          linter: {
            echo "flake8"
          }
        )
      }
    }

    stage ("Upload") {
      steps {
        withCredentials([usernamePassword(credentialsId: "dockerhub-token", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
          sh "echo $PASSWORD | docker login -u $USERNAME --password-stdin"

          // TODO: mejorar con script
          sh "docker push mario21ic/dmc-api:${env.BUILD_NUMBER}"

          sh "docker logout"
        }
      }
    }

  }
}
