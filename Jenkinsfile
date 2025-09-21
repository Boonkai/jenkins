pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url:'https://github.com/Boonkai/jenkins.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 --version'
                sh 'python3 script.py'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy step (placeholder)'
            }
        }
    }
}
