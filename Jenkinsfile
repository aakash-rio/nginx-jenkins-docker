pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nginx-jenkins .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop nginx-container || true
                docker rm nginx-container || true
                docker run -d -p 80:80 --name nginx-container nginx-jenkins
                '''
            }
        }
    }
}
