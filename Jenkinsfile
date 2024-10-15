pipeline {
    agent {
        docker { 
            image 'node:20.18.0-alpine3.20' 
            args '-v $HOME:/home/jenkins'
        }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}