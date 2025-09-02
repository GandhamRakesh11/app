pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "gandhamfullstack-nginx"
        DOCKER_CONTAINER = "nginx"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/GandhamRakesh11/app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $DOCKER_IMAGE .
                '''
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop $DOCKER_CONTAINER || true
                docker rm $DOCKER_CONTAINER || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d --name $DOCKER_CONTAINER \
                -p 80:80 -p 443:443 \
                -v /etc/letsencrypt:/etc/letsencrypt:ro \
                $DOCKER_IMAGE
                '''
            }
        }
    }
}
