pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
               git 'https://github.com/nttugit/nodejs-hello'  
            }
        }
        
        stage('Build') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                    // Authenticate with the Docker registry
                    withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
                      bat 'docker build -t nicenguyen/nodejs-hello:v1 .'
                      bat 'docker push nicenguyen/nodejs-hello:v1'
                    }
            }
        }
    }

}
