pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
               git branch: 'main', url: 'https://github.com/Groot2308/getting-started-todo-app.git'
            }
        }
    }
}