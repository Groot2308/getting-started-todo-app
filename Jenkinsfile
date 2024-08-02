pipeline {
    agent any
    environment {
        SONARQUBE_SCANNER_HOME = tool 'sonarqubedemo'
    }
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Groot2308/getting-started-todo-app.git'
            }
        }
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Local SonarQube') {
                    sh '${SONARQUBE_SCANNER_HOME}/bin/sonar-scanner'
                }
            }
        }
    }
}
