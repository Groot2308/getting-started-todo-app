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
                SCANNER_HOME = tool 'scanner'
            }
            steps {
                withSonarQubeEnv(installationName: 'sonarqubedemo') {
                    sh '''
                    $SCANNER_HOME/bin/sonar-scanner \
                      -Dsonar.projectKey=getting-started-todo-app \
                      -Dsonar.sources=. \
                      -Dsonar.host.url=http://172.27.0.9:9000 \
                      -Dsonar.login=squ_32f68c911cdd370eb8dcec9a4b109e30d494b17d
                    '''
                }
            }
        }
    }
}
