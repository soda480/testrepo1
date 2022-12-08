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
          steps {
            sh 'env'
          }
        }
    }
}
