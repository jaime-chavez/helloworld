pipeline {
    agent any
    stages {
        stage('install') {
            steps {
                npm install
            }
        }
        stage('run'){
            steps{
                npm start
            } 
        }
    }
}


// node {
//     echo "My branch is:"
// }