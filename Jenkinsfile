pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker container...'
                sh 'docker-compose down'
                sh 'docker-compose up -d'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the API...'
                sh 'curl -X POST http://localhost:5001/styleTransfer -F "image=@test.jpg" --output styled_output.jpg'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment successful!'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
