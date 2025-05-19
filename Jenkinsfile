pipeline {
    agent {
        docker {
            image 'node:18'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
            reuseNode true
        }
        retries 2  // Retry the whole agent block if Jenkins restarts
    }

    environment {
        DOCKER_BUILDKIT = 1
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Backend') {
            steps {
                sh 'cd backend && npm install'
            }
        }

        stage('Build Frontend') {
            steps {
                sh 'cd frontend && npm install'
            }
        }

        stage('Docker Compose Up') {
            steps {
                sh 'docker compose up -d --build'
            }
        }
    }

    post {
        always {
            sh 'docker compose down'
        }
    }
}
