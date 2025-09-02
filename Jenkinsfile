pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/GandhamRakesh11/app.git'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo rm -rf /usr/share/nginx/html/*
                sudo cp index.html /usr/share/nginx/html/
                sudo systemctl reload nginx
                '''
            }
        }
    }
}
