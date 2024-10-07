pipeline {
    agent any
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!'
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "${env.aws-key}"
            }
        }
    }
}

