pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/PankajaDesai/flask-app-devops.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("flask-app-devops:latest")
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    docker.image("flask-app-devops:latest").run('-d -p 5000:5000')
                }
            }
        }
    }
}

