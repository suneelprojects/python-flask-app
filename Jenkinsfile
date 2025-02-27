pipeline {
    agent any
    stages {
        stage('Code') {
            steps {
                echo 'Cloning Repository'
                git branch: 'main', url: 'https://github.com/Spandana115/python-flask-app.git'

            }
        }

        stage('Install') {
            steps {
                echo 'Building Docker Image'
                sh 'docker build -t flask-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests'
                sh 'docker run --rm flask-app pytest test_app.py'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Container'
                sh 'docker run -itd --name flask-container -p 5000:5000 flask-app'
            }
        }
    }
}
