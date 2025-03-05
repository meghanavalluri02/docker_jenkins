pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'meghanavalluri/my-flask-app:latest'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url:'https://github.com/meghanavalluri02/docker_jenkins.git',branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-creds', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}
