pipeline {
    agent any
    tools {
        // Specify the SonarScanner tool name you configured in Jenkins
        // This should match the name you entered in the global tool configuration
        sonarScanner 'SonarScanner'
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from Git
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // Run SonarScanner with the configured tool
                script {
                    def scannerHome = tool 'SonarScanner'
                    def scannerBat = bat(script: "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=bhushan08", returnStatus: true)
                    if (scannerBat != 0) {
                        error "SonarScanner analysis failed"
                    }
                }
            }
        }
    }
}

