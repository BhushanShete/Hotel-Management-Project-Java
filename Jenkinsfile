pipeline {
    agent any
    
    stages {
        stage('SCM') {
            steps {
                // Checkout the code from Git
                checkout([$class: 'GitSCM', 
                          branches: [[name: '*/master']], 
                          doGenerateSubmoduleConfigurations: false, 
                          extensions: [], 
                          submoduleCfg: [], 
                          userRemoteConfigs: [[url: 'https://github.com/BhushanShete/Hotel-Management-Project-Java.git']]])
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                // Set up environment variables for SonarQube
                withSonarQubeEnv('bhushan') {
                    // Run Maven build
                    bat script: 'mvn clean verify sonar:sonar -Dsonar.projectKey=bhushan -Dsonar.projectName=\'bhushan\'', 
                        // Use the correct Maven installation defined in Jenkins global configuration
                        bat script: 'mvn clean verify sonar:sonar -Dsonar.projectKey=bhushan -Dsonar.projectName=\'bhushan\''
                }
            }
        }
    }
}

