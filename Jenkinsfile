pipeline {
    agent 'node'
    stages {
        stage('install') {
            steps {
                npm install
            }
        }
        stage('run'){
            npm start
        }
    }
}


// node {
//     echo "My branch is:"
// }