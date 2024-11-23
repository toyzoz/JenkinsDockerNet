pipeline {
    agent any
     environment {
        DOCKER_IMAGE = 'jenkins-docker-net'
        DOCKER_TAG = 'latest' 
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                 script {
                    sh "docker build -f JenkinsDockerNet/Dockerfile -t ${DOCKER_IMAGE}:${DOCKER_TAG} ."
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                 script {
                    sh "docker run -d -p 80801:8080 --name ${DOCKER_IMAGE} ${DOCKER_IMAGE}:${DOCKER_TAG}"
                }
            }
        }
    }
}