// pipeline {
//     agent { any { image 'node:12.16.2' args '-p 3000:3000' } }
//     stages {
//         stage('Test') {
//             steps {
//                 sh 'node --version'
//             }
//         }
//     }
// }



pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                any {
                    image 'gradle:8.2.0-jdk17-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'gradle --version'
            }
        }
    }
}