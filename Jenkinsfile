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
        stage('Build') {
          when {
            anyOf {
              allOf {
                expression { env.GIT_BRANCH == 'main' }
                triggeredBy 'TimerTrigger'
              }
              triggeredBy 'UserIdCause'
              triggeredBy 'SCMTrigger'
            }
          }
          steps {
            sh 'env'
          }
        }
    }
}
