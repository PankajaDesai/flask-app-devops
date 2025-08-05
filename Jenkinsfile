pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-app"
        CONTAINER_NAME = "flask-container"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/PankajaDesai/flask-app-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'podman build -t $IMAGE_NAME app/'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                podman stop $CONTAINER_NAME || true
                podman rm $CONTAINER_NAME || true
                podman run -d -p 5000:5000 --name $CONTAINER_NAME $IMAGE_NAME
                '''
            }
        }
    }
}


