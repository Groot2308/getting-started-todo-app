pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-hubregistry')
    }
    
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
                      -Dsonar.host.url=http://172.29.0.9:9000 \
                      -Dsonar.token=squ_32f68c911cdd370eb8dcec9a4b109e30d494b17d
                    '''
                }
            }
        }  

        stage('Check Docker Path') {
            steps {
                sh 'echo $PATH'
                sh 'which docker'
            }
        }  


        stage('Build') {
            steps {
                sh 'docker build -t danghoan2308/todoapp:latest .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Push') {
            steps {
               sh 'docker push danghoan2308/todoapp:latest'
            }
        }
    }
}
