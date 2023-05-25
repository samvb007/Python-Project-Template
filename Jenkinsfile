node {
  stage('SCM') {
    checkout scm
  }
    stage('SonarQube Analysis') {
      withSonarQubeEnv('sonarqube-server') {
        sh "/opt/sonar_scanner/sonar-scanner-4.0.0.1744-linux/bin/sonar-scanner -Dsonar.projectKey=Python-Project-Template -Dsonar.sources=. "
    }
  }
}
