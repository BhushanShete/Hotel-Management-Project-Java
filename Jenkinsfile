node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      bat "${mvn}/bin/mvn.cmd clean verify sonar:sonar -Dsonar.projectKey=bhushan -Dsonar.projectName='bhushan'"
    }
  }
}
