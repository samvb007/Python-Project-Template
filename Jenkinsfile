node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner'
    withSonarQubeEnv(credentialsId: 'SONAR_TOKEN_dup') {
        sh "${scannerHome}/bin/sonarqube-scanner"
    }
  }
}
