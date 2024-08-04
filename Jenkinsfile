pipeline {
    agent any
    // environment {
    //     DOCKERHUB_CREDENTIALS = credentials('docker-hubregistry')
    // }
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
                withSonarQubeEnv('sonarqubedemo') {
                    sh '''
                    $SCANNER_HOME/bin/sonar-scanner \
                      -Dsonar.projectKey=getting-started-todo-app \
                      -Dsonar.sources=. \
                      -Dsonar.host.url=http://172.18.0.9:9000 \
                      -Dsonar.login=squ_d069760d5608a8af0b2abcddbed5af71bf0bd1d7
                    '''
                }
            }
        }
        // stage('Check Docker Path') {
        //     steps {
        //         sh 'echo $PATH'
        //         sh 'which docker'
        //     }
        // }
        // stage('Build') {
        //     steps {
        //         script {
        //             if (fileExists('/var/run/docker.sock')) {
        //                 sh 'docker build -t danghoan2308/todoapp:latest .'
        //             } else {
        //                 error 'Docker daemon không chạy hoặc không thể truy cập Docker socket.'
        //             }
        //         }
        //     }
        // }
        // stage('Login') {
        //     steps {
        //         script {
        //             withCredentials([usernamePassword(credentialsId: 'docker-hubregistry', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
        //                 sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
        //             }
        //         }
        //     }
        // }
        // stage('Push') {
        //     steps {
        //         sh 'docker push danghoan2308/todoapp:latest'
        //     }
        // }
    }
}
