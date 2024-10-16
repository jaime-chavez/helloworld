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


// NodeJS plugin https://plugins.jenkins.io/nodejs/   configurar en tools
// GCloud SDK https://plugins.jenkins.io/gcloud-sdk/

// pipeline {
//     agent {
//         docker {
//             image 'node:lts-buster-slim'
//             args '-p 3000:3000'
//         }
//     }
    // environment {
    //     CI = 'true'
    // }
    // stages {
    //     stage('Build') {
    //         steps {
    //             dir('src/react') {
    //                 sh 'npm install'
    //             }
    //         }
    //     }
        // stage('Test') {
        //     steps {
        //         sh './jenkins/scripts/test.sh'
        //     }
        // }
        // stage('Deliver') {
        //     steps {
        //         sh './jenkins/scripts/deliver.sh'
        //         input message: 'Finished using the web site? (Click "Proceed" to continue)'
        //         sh './jenkins/scripts/kill.sh'
        //     }
        // }
//     }
// }