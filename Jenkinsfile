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
/*
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
*/
/*
pipeline {
    agent any
    stages {
        
        stage('Clone sources') {
            steps {
                git url: 'https://github.com/DanteAnnetta/dds-deploy.git'
            }
        }
        
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''${scannerHome}/bin/sonar-scanner'''
                }
            }
        }
        
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
        
        
    }
}
*/

//START-OF-SCRIPT
node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=dds-deploy -Dsonar.projectName='dds-deploy'"
    }
  }
}
//END-OF-SCRIPT
