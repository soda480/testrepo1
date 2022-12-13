pipeline {    
  agent { 
        label 'rbhe'
    }
    options {
        disableConcurrentBuilds()
    }
    triggers {
        cron('TZ=US/Arizona\nH * * * *')
    }
    stages {
      stage('Prep') {
        steps {
          sh 'sleep 60'
        }
      }
      stage('Code Scan Pipeline') {
         when {
          anyOf {
            allOf {
              expression { env.GIT_BRANCH == 'main' }
              triggeredBy 'TimerTrigger'
            }
            triggeredBy 'UserIdCause'
            triggeredBy 'BranchIndexingCause'
          }
         }
        stages {
          stage('Build Docker Images') {
            steps {
              echo 'Build Docker Image'
              sh 'sleep 10'
            }
          }
          stage('Prep Code Scan') {
            steps {
              echo 'Prep Code Scan'
              sh 'sleep 10'
            }
          }
          stage('Code Scan') {
            steps {
              echo 'Code Scan'
              sh 'sleep 10'
            }
          }
        }
      }
      stage('Publish') {
        when {
          expression { env.GIT_BRANCH ==~ /^(?:test.*)$/}
        }
        steps {
          echo 'Publish'
          sh 'sleep 10'
        }
      }
    }
}


