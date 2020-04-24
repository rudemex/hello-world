pipeline {
  agent any


  options {
    timeout(time: 2, unit: 'MINUTES')
  }

  stages {
    stage('Deploy') {
      steps {
        sh 'GET CREDENTIALS'
        withCredentials([usernamePassword(credentialsId: 'MT-FTP', passwordVariable: 'FTP_PASSWORD', usernameVariable: 'FTP_USERNAME')]) {
          sh 'UPLOAD FTP - $DOMAIN'
          sh 'git ftp $TYPE --user $FTP_USERNAME --passwd $FTP_PASSWORD ftp://s222943.gridserver.com/domains/$DOMAIN/html/'
        }
      }
    }
  }
  
  post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
  
}
