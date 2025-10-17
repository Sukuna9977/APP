pipeline {
    agent any
    
    stages {
        stage('SCM Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                timeout(time: 5, unit: 'MINUTES') {
                    script {
                        def scannerHome = tool 'SonarScanner'
                        withSonarQubeEnv('SonarQube') {
                            sh "${scannerHome}/bin/sonar-scanner"
                        }
                    }
                }
            }
        }
    }
}
