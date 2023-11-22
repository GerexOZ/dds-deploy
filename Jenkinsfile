/*pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                def scannerHome = tool 'SonarQubeScanner3'
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
*/
/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'maven:3.9.5-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}
