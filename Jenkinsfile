#!groovy

/* Declarative pipeline */
pipeline {
  agent {
    node {
      label 'master'
      customWorkspace 'workspace/letsencrypt'
    }
  }
  stages {
    stage('Prepare environment') {
      steps {
        sh 'molecule create'
        sh 'molecule converge'
      }
    }

    stage('Run Tests'){
      steps {
        sh 'molecule syntax'
        sh 'molecule idempotence'
        sh 'molecule verify'
      }
    }
  }

  post {
    always {
      sh 'molecule destroy'
    }
    success {
      mattermostSend color: 'good', message: "Job ${JOB_NAME} ${BUILD_NUMBER} ($gitlabActionType) has finished successfully (<${BUILD_URL}|Open>)"
    }
    failure {
      mattermostSend color: 'danger', message: "Job ${JOB_NAME} ${BUILD_NUMBER} has failed(<${BUILD_URL}|Open>)"
    }
  }
}