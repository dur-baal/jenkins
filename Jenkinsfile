#!/usr/bin/env groovy

A_LOG_FILE = 'stage_log.log'

pipeline {
  agent any

  stages {
    stage("Build") {
      steps {
        sh 'mvn -v'
        script{
          directory_listing = sh ( script: "ls ./", returnStdout: true).trim()
          echo "files listed here is - ${directory_listing}"
        }
      }
    }

/*
    stage("Testing") {
      parallel {
        stage("Unit Tests") {
          agent { docker 'openjdk:7-jdk-alpine' }
          steps {
            sh 'java -version'
          }
        }
        stage("Functional Tests") {
          agent { docker 'openjdk:8-jdk-alpine' }
          steps {
            sh 'java -version'
          }
        }
        stage("Integration Tests") {
          steps {
            sh 'java -version'
          }
        }
      }
    }
*/
    stage("Deploy") {
      steps {
        tee(A_LOG_FILE){
          echo "Deploy!"
        }
      }
    }
  }
}
