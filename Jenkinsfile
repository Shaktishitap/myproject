pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Checkout source code
                checkout scm

                // Build Docker image
                sh 'docker build -t nginx .'
            }
        }

        stage('Test') {
            steps {
                // Run tests inside Docker container
                sh 'docker run nginx npm test'
            }
        }

        stage('Deploy') {
            steps {
                // Push Docker image to registry
                sh 'docker push nginx'

                // Deploy to production
                sh 'kubectl apply -f your_deployment.yaml'
            }
        }
    }
}

