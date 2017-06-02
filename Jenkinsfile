#!groovy

pipeline {

  try {
    ws('workspace/letsencrypt') {
      stage('Checkout code') {
        sh 'echo "${BUILD_CAUSE}"'
        checkout scm
      }

      stage('Prepare environment') {
        step('Installing Molecule') {
          sh 'sudo pip install molecule'
        }

        step('Creating Containers') {
          sh 'molecule create'
        }

        step('Installing the Role') {
          sh 'molecule converge'
        }
      }

      stage('Run Tests'){
        stage('Syntax check') {
          sh 'molecule syntax'
        }

        stage('Idempotence check') {
          sh 'molecule idempotence'
        }

        step('Verify the application') {
          sh 'molecule verify'
        }
      }

      stage('Cleanup') {
        sh 'molecule destroy'
      }

      stage('Accept merge and notify') {
        /* todo Create a way to accept pull request and tag it as a new release
        if(gitlabActionType.equals("MERGE")){
          addGitLabMRComment comment: 'Accepted by Jenkins job'
          acceptGitLabMR()
          withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'ae0c7238-650a-4f74-bf1a-1c4f526fa908', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD']]) {
            sh("git tag -a $VERSION -m 'Automatic Release'")
            sh('git push http://${GIT_USERNAME}:${GIT_PASSWORD}@<OUR_GITLAB_SERVER_URL>/${gitlabSourceNamespace}/${gitlabSourceRepoName}.git --tags')
          }
        }
        */
        mattermostSend color: 'good', message: "Job ${JOB_NAME} ${BUILD_NUMBER} ($gitlabActionType) has finished successfully (<${BUILD_URL}|Open>)"
      }
    }
  }

  catch (err) {
    stage('Notify about failure') {
      mattermostSend color: 'danger', message: "Job ${JOB_NAME} ${BUILD_NUMBER} has failed(<${BUILD_URL}|Open>)"
      /*currentBuild.result = "FAILURE"*/
      throw err
    }
  }
}