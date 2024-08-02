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
        stage('Scan') {
            steps {
                withSonarQubeEnv(installationName: 'sonarqubedemo') {
                    // sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar'
                       sh '${SONARQUBE_SCANNER_HOME}/bin/sonar-scanner'
                }
            }
        }
    }
}
