pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Checkout source code
                checkout scm

                // Build Docker image
                sh 'docker build -t Dockerfile .'
            }
        }

        stage('Test') {
            steps {
                // Run tests inside Docker container
                sh 'docker run Dockerfile npm test'
            }
        }

        stage('Deploy') {
            steps {
                // Push Docker image to registry
                sh 'docker push Dockerfile'

                // Deploy to production
                sh 'kubectl apply -f your_deployment.yaml'
            }
        }
    }
}

