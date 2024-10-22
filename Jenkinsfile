pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/LabharthBagda/Jenkins.git'
            }
        }
        stage('List Files') {
            steps {
                script {
                    // List files and directories in the workspace
                    def files = bat(script: 'dir', returnStdout: true)
                    echo "Files in the workspace:\n${files}"
                }
            }
        }
        stage('Build') {
            steps {
                bat 'javac Main.java'  // Adjust this if Main.java is in a subdirectory
            }
        }
        stage('Run') {
            steps {
                bat 'java Main'  // Adjust this if Main.class is in a subdirectory
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
