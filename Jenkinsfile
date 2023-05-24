node {
  stage('SCM') {
    checkout scm
  }
    stage('SonarQube Analysis') {
      withSonarQubeEnv(credentialsId: 'SONAR_TOKEN_dup') {
        sh "/opt/sonar_scanner/sonar-scanner-4.0.0.1744-linux/bin/sonar-scanner -Dsonar.projectKey=Project_Template -Dsonar.sources=. "
    }
  }
}
