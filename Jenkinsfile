// Docker plugoin
// Docker commons
// Docker multibranch


pipeline {
    agent {
        docker { image 'node:20.18.0-alpine3.20' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}



// pipeline {
//     agent any
//     stages {
//         stage('Build') {
//             agent {
//                 any {
//                     image 'gradle:8.2.0-jdk17-alpine'
//                     reuseNode true
//                 }
//             }
//             steps {
//                 sh 'gradle --version'
//             }
//         }
//     }
// }


// pipeline {
//     agent { dockerfile true }
//     stages {
//         stage('Test') {
//             steps {
//                 sh 'node --version'
//                 sh 'svn --version'
//             }
//         }
//     }
// }