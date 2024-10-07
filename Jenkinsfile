// https://plugins.jenkins.io/multibranch-build-strategy-extension/
// https://plugins.jenkins.io/google-storage-plugin/
// https://plugins.jenkins.io/build-timestamp/#:~:text=Export%20build%20timestamps%20to%20build%20env


pipeline {
     agent any
     environment {
        CREDENTIALS_ID ='labkey' //configurar en credentials,  como Google Service Account from private key
        BUCKET = 'jenkinsbucketlab' 
        LOG = "log_${BUILD_TIMESTAMP}.txt" //configurar en system
    }
     stages {
        stage('Copy files to GCS') {
            steps {
                executeFileCopy()
            }
        }
     }
     post {
        always {
            step([$class: 'StdoutUploadStep', credentialsId: env.CREDENTIALS_ID,  bucket: "gs://${env.BUCKET}/logs", logName: env.LOG])
        }
    }
}

void executeFileCopy() {
    def allFiles = getChangedFilesList()

    allFiles.each { file -> 
        echo("---- COPY ${file.toUpperCase()} ----")                                  
        stage(file) {
            step([$class: 'ClassicUploadStep', credentialsId: env.CREDENTIALS_ID,  bucket: "gs://${env.BUCKET}", pattern: "${file}"])
        }

    }
}

@NonCPS
List<String> getChangedFilesList(){
    def changedFiles = []
    for ( changeLogSet in currentBuild.changeSets){
        for (entry in changeLogSet.getItems()){
            changedFiles.addAll(entry.affectedPaths)
        }
    }
    if (changedFiles.indexOf("Jenkinsfile") != -1)
        changedFiles.remove(changedFiles.indexOf("Jenkinsfile"))
    return changedFiles
}
