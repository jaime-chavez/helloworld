pipeline {
     agent any
     environment {
        DO_BUILD_PACKAGES = 'true'
     }
     stages {
        stage('Trigger Building') {
            when {
                environment(name: 'DO_BUILD_PACKAGES', value: 'true')
            }
            steps {
                executeModuleScripts('build')
            }
        }
     }
}

void executeModuleScripts(String operation) {
    def allModules = ['module1', 'module2', 'module3', 'module4', 'module11']

    allModules.each { module ->  
        String action = "${operation}:${module}"  
        
        echo("---- ${action.toUpperCase()} ----")        
        String command = echo "${action}"                   
                
        script {
            stage(module) {
                bat(command)
            }
        }
    }
}






// pipeline {
//     agent any
//     environment {
//         CREDENTIALS_ID ='labkey'  //Google Cloud Storage plugin https://plugins.jenkins.io/google-storage-plugin/
//         BUCKET = 'jenkinsbucketlab' 
//         LOG = "log_${BUILD_TIMESTAMP}.txt" //Build Timestamp Plugin https://plugins.jenkins.io/build-timestamp/#:~:text=Export%20build%20timestamps%20to%20build%20env
//     }
//     stages {
//         stage('Stage 1') {
//             steps {
//                 echo 'Hello world!'
//                 echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
//                 echo "logfile name ${LOG}"
//             }
//         }
//         stage('Get Last Commit Details') {
//             steps {
//                 script{
//                     List<String> changes = getChangedFilesList()
//                     println ("Changed file list: " + changes)
//                     Integer jenkinsIndex = changes.indexOf("Jenkinsfile")
//                     changes.remove(jenkinsIndex)
//                     println ("List without jenkisfile: " + changes)
//                     changes.each {
//                         println "list: ${it}"
//                     }
//                 }
//             }
//         }
//         stage('Store to GCS') {
//             steps{
//                 //step([$class: 'ClassicUploadStep', credentialsId: env.CREDENTIALS_ID,  bucket: "gs://${env.BUCKET}", pattern: "files/*"])
//                 step([$class: 'ClassicUploadStep', credentialsId: env.CREDENTIALS_ID,  bucket: "gs://${env.BUCKET}", pattern: ["files/uno.yaml"]])
//             }
//         }
//     }
//     post {
//         always {
//             // Uploads build log with name LOG as an object to our GCS bucket.
//             step([$class: 'StdoutUploadStep', credentialsId: env.CREDENTIALS_ID,  bucket: "gs://${env.BUCKET}/logs", logName: env.LOG])
//         }
//     }
// }

// @NonCPS
// List<String> getChangedFilesList(){
//     def changedFiles = []
//     for ( changeLogSet in currentBuild.changeSets){
//         for (entry in changeLogSet.getItems()){
//             changedFiles.addAll(entry.affectedPaths)
//         }
//     }
//     return changedFiles
// }
