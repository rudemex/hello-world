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
  
}
