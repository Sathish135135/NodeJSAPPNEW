pipeline {
    agent any
    environment {
        NODE_HOME = '/usr/local/bin/node'
        PATH = "$NODE_HOME:$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Sathish135135/NodeJSAPPNEW.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    sh 'npm test' // You should add test scripts in your Node app
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t MynodeDoc:latest .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    sh 'docker tag mynodeDoc:latest your-dockerhub-username/mynodeDoc:latest'
                    sh 'docker push your-dockerhub-username/mynodeDoc:latest'
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
