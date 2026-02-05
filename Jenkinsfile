pipeline {
  agent any

  tools {
    jdk 'JDK17'
    ant 'ANT'
    sonarScanner 'SonarScanner'
  }

  stages {
    stage('Clone') {
      steps { checkout scm }
    }

    stage('Compile') {
      steps {
        sh 'ant clean'
        sh 'ant compile'
      }
    }

    stage('Tests') {
      steps { sh 'echo "No tests configured"' }
    }

    stage('Package') {
      steps { sh 'ant jar || ant dist' }
    }

    stage('SonarQube') {
      steps {
        withSonarQubeEnv('SonarLocal') {
          sh """
            ${tool 'SonarScanner'}/bin/sonar-scanner \
              -Dsonar.projectKey=gestion-bancaire \
              -Dsonar.projectName="Gestion Bancaire" \
              -Dsonar.sources=src \
              -Dsonar.java.binaries=build/classes
          """
        }
      }
    }
  }
}
