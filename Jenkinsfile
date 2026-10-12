pipeline{
    agent any
    stages{
        stage('clone rerepository') {
            steps {
                git url: 'https://github.com/Ravina-Duggal/bicycle_backend.git', branch: 'main'
            }
        }
        stage('docker build') {
            steps { 
                sh 'docker build -t backend .'
            }
        }
       stage('delete old container'){
            steps{
                sh 'docker stop backend-container || true'
                sh 'docker rm backend-container || true'
            }
        }
        stage('Deploy') {
            steps {
               sh 'docker run -d --name backend-container -p 3015:3015 backend'
            }
        }
    }
}
