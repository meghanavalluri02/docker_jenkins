pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'barathkumar29/my-flask-app:latest'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/jkbarathkumar/jenkins_with_docker2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}
