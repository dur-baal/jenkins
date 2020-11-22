#!/usr/bin/env groovy

A_LOG_FILE = 'stage_log.log'

pipeline {
  agent any

  stages {
    stage("Build") {
      steps {
        script {
          def output
            try {
            timeout(time: 5, unit: 'SECONDS') {
              try {
                sleep(30)
              }
              catch (err) {
                echo "For some reason, this catch is activated. Error: ${err.getMessage()}"
              }
              echo "This should not be executed, but it is!"
            }
          }
          catch (err) {
            echo "I expect that this catch will be activated. Error: ${err.getMessage()}"
          }
          sh 'mvn -v'
          def file_name = sh "ls ./"
          echo "file_name"
          echo sh(script:'env|sort', returnStdout: true)
          echo "${env.BUILD_URL}campenta_20System_20Documentation"
        }
      }
    }

    stage("Deploy") {
      steps {
        tee(A_LOG_FILE){
          echo "Deploy! and check"
        }
      }
    }
  }
}
