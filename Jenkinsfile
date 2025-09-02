pipeline {
    agent any

    environment {
        DOCKER_CONTAINER = "nginx-dashboard"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/GandhamRakesh11/app.git'
            }
        }

        stage('Deploy') {
            steps {
                sh """
                docker cp index.html $DOCKER_CONTAINER:/usr/share/nginx/html/index.html
                docker exec $DOCKER_CONTAINER nginx -s reload
                """
            }
        }
    }
}

