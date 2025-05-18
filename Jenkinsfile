pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Hadia2003/docker-mysql-nodejs-reactjs-app.git'
            }
        }
        stage('Build Docker Containers') {
            steps {
                script {
                    sh 'docker-compose -p devops-jenkins -f docker-compose.yml up -d --build'
                }
            }
        }
    }
}
