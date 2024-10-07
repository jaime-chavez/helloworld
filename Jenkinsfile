pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('secret-key')
    }
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!'
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                withCredentials([string((credentialsId: 'secret-key', variable: 'TOKEN'))])
                echo "${TOKEN}"
            }
        }
    }
}

