pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/LabharthBagda/TestRepo.git'
            }
        }
        stage('List Files') {
            steps {
                bat 'dir'  // For Windows
            }
        }
        stage('Build') {
            steps {
                bat 'javac Main.java'
            }
        }
        stage('Run') {
            steps {
                bat 'java Main'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}


