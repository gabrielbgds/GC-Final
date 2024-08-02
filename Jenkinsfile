pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/gabrielbgds/GC-Final'
            }
        }
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build("meu-app:latest")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    dockerImage.inside {
                        sh 'make test' 
                    }
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
