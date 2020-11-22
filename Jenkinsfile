#!/usr/bin/env groovy

A_LOG_FILE = 'stage_log.log'

pipeline {
  agent any

  stages {
    stage("Build") {
      steps {
        script {
          def output
          try{
          timeout(time: 5, unit: 'SECONDS', activity: true){
            sleep(5)
          }
          }catch (any){
            output = any.toString()
          } finally {
            echo "hi there 2!!! - '${output}'"
          }
          sh 'mvn -v'
          def file_name = sh "ls ./"
          echo "file_name"
        }
      }
    }

    stage("Deploy") {
      steps {
        tee(A_LOG_FILE){
          echo "Deploy!"
        }
      }
    }
  }
}
