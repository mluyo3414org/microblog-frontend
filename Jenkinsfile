pipeline {
  agent none
  options { 
    buildDiscarder(logRotator(numToKeepStr: '10'))
    skipDefaultCheckout true
  }
  stages('Node Test')
  {
    stage('Node Tests') {
      agent {
        kubernetes {
          label 'nodejs'
       }
      }
      steps {
            checkout scm           
            container('nodejs-container') {
              sh '''
                 yarn install
                 yarn test:unit
                 '''
            }
      } 
    }
  }
}
