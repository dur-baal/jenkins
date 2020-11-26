#!/usr/bin/env groovy

A_LOG_FILE = 'stage_log.log'

pipeline {

  triggers {
    cron('34 09 * * 1-5')
  }

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
        sh 'java -version'
//        tee(A_LOG_FILE){
//          echo "WARNING in /var/jenkins/cpp.c (at line: 2) The file contains TAB character, not good."
//        }
//        recordIssues(tools: [groovyScript(id: 'id-vhdl-warning', parseId: 'id-vhdl-warnings', pattern: A_LOG_FILE, reportEncoding: 'UTF-8')])
      }
    }
  }
}
