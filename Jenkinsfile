pipeline {
    agent any

    tools {
        jdk 'JDK17'
        ant 'ANT'
    }

    stages {

        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                sh 'ant clean'
                sh 'ant compile'
            }
        }

        stage('Tests') {
            steps {
                sh 'echo "No tests configured"'
            }
        }

        stage('Package') {
            steps {
                sh 'ant jar || ant dist'
            }
        }

        stage('SonarQube') {
            steps {
                sh 'echo "Sonar later"'
            }
        }
    }
}
