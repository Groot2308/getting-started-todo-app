pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Groot2308/getting-started-todo-app.git'
            }
        }
        stage('SonarQube analysis') {
            environment {
                SCANNER_HOME ='sonarqubedemo'
            }
            steps {
                withSonarQubeEnv(installationName: 'sonarqubedemo') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner'''
                }
            }
        }
    }
}
