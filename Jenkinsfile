node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
      withSonarQubeEnv(credentialsId: 'SONAR_TOKEN_dup') {
        sh "sonarqube-scanner \
              -Dsonar.projectKey=sonar-dup \
              -Dsonar.sources=. \
              -Dsonar.host.url=http://172.17.0.2:9000 "
    }
  }
}
