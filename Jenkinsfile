node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqube-scanner'
    withSonarQubeEnv(credentialsId: 'SONAR_TOKEN_dup') {
        sh "${scannerHome}/bin/sonarqube-scanner"
    }
  }
}
